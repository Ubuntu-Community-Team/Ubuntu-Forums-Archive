---
title: "lex &amp;yacc"
date: 2010-10-27
forum: General Help
---

### Post by rumshenoy on 2010-10-27
Why does the input I give to lex & yacc repeat itself?
I am building a syntax analyser in lex yacc specifically for built in functions. The line of input that i give repeats itself ,once I type the input and press "Enter"(most of the time it is half the input) for eg.
int n=sqrt(3);
int n=);(this is repeated)
on pressing control D then.. it issues a valid or invalid. Why does this happen?
Secondly,yyparse() only for a single line of input.How do i make it work for a text with no "repeating input errors" and no pressing of "control d".
Thirdly,How do i put this input in a file and get the same line by line output.
Fourthly,I came across one more problem,under math functions i am trying to recognise the syntax of pow and sqrt function. it seems that my lex &yacc confuse and give a "valid" for an input like "int p=pow(3);" which i have absolutely not specified anywhere and is clearly invalid..
I also want to include string functions in this..
Please help. I have to submit this program tomo!!!!

---

