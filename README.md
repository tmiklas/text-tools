text-tools
==========

Miscellaneous text tools I worte to use in my projects, because sharing is caring :-)

trigrams.pl
-----------

From http://en.wikipedia.org/wiki/Trigram

> Trigrams are a special case of the N-gram, where N is 3. They are often used in natural language processing for doing statistical analysis of texts. 

This is an English language implementation of trigrams I wrote about a year ago when playing with some crypto challenges (problem was how to programatically tell when key bruteforce attempt produced English-like plaintext). This is just a bit more complex idea than frequency analysis of individual letters.
These days I use it mostly to process output from <code>strings</code> command and find English-like meaningful text instead sifting manually through thousands of lines of output.
The more English-like the text is, the higher the score. The script may not be blazing fast but it's still much better than manual review of unsorted output.

Example:

	strings /bin/bash | sort | uniq | trigrams.pl | sort -r 

Ouput: 

	001654	    to indices 0 and 1 of an array variable NAME in the executing shell.
	001648	    PROMPT_COMMAND	A command to be executed before the printing of each
	001638	    The format is re-used as necessary to consume all of the arguments.  If
	001618	    entries in $PATH are used to find the directory containing FILENAME.
	001606	    ARG is a command to be read and executed when the shell receives the
	001603	    is trapped and flagged as an error.  The following list of operators is
	001597	    only to the function where they are defined and its children.
	...
	000000	=^#'
	000000	=^/+
	000000	=`.-
	000000	<$/@
	000000	<>;&|$
	000000	~&<-
	000000	~@<{

The <code>sort</code> is ran twice because <code>uniq</code> doesn't do it's job very well and <code>sort -r</code> will return multiple identical lines. Of course it's cheaper (in terms of CPU time) to run <code>sort</code> before <code>trigrams.pl</code> where all heavy lifting happens.

LICENSE
-------

Please check the script source for licensing information - each script can be different in this respect but all will have licensing information available.

CONTACT
-------

You can contact me via GitHub or find me on Twitter as [@tomaszmiklas](https://twitter.com/tomaszmiklas)
