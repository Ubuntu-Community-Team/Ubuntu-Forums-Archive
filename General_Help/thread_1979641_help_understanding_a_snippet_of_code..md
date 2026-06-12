---
title: "help understanding a snippet of code."
date: 2012-05-13
forum: General Help
---

### Post by spiritech on 2012-05-13
[FONT=monospace]below is some code i used to rename some files. it removed the last 11 digits of the code terminated with .mp4.

[/FONT]rename 's/.{11}\.mp4$/.mp4/'  * 

[FONT=monospace]could someone be a little verbose and explain to me roughly how the code worked and what some of the symbols mean?

does the 's mean search. and what do the / and \ do?

spiritech
[/FONT]

---

### Post by Vaphell on 2012-05-13
it works with so called regular expressions describing the pattern in an abstract, flexible way

s = substitute
s/pattern/replacement/
/ is a separator here, but i think any char can be used for that

\ is used to escape the character, dot in this case. Dots by default mean any-char so if you mean literal dot, you need to add \ to make sure program will ignore it.

what it does is replace (11 chars).mp4 at the end ($) with .mp4, in other words remove 11 chars before the extension 

.{11} = any 11-char long sequence, (.=any char)
\. = literal dot, not any-char dot
$ = end of line marker

---

### Post by billyseth on 2012-05-13
here is a site with some other examples of regular expressions, they are a pretty powerful tool for any sort of matching/replacing/renaming that you need to do.

[http://www.regular-expressions.info/examples.html](http://www.regular-expressions.info/examples.html)

---

### Post by spiritech on 2012-05-13
so, say i wanted to remove the first 11 digits of the files. would this be right?

rename 's/$.{11}/ / *

if not what  character is used to indicate beginning and how would you substitute with nothing.
i used the $ to indicate the at the bigining. and a space to to substitute the digit for nothing.

what does the * do?

---

### Post by spiritech on 2012-05-13
> **billyseth said:**
> here is a site with some other examples of regular expressions, they are a pretty powerful tool for any sort of matching/replacing/renaming that you need to do.

[http://www.regular-expressions.info/examples.html](http://www.regular-expressions.info/examples.html)

thank you i will have a read through. i am trying to learn a little bit of bash as well. looks like all these things can be used together when writing scripts.

---

### Post by steeldriver on 2012-05-13
Good try! in fact to replace with nothing, you put - literally - nothing between the separators i.e. just // (no space)

Also $ has a special meaning (inherited from sed - the stream editor) that is "end of line". The equivalent for "beginning of line" is the carat character ^, so to remove the *leading* 11 characters you'd want

```
rename 's/^.{11}//' *
```BTW if you add a -v switch (option) to rename you can confirm what it's doing

regex is always a learning experience for me - nice to see someone who likes to get under the hood with this stuff, good luck

---

### Post by spiritech on 2012-05-13
> **steeldriver said:**
> Good try! in fact to replace with nothing, you put - literally - nothing between the separators i.e. just // (no space)

Also $ has a special meaning (inherited from sed - the stream editor) that is "end of line". The equivalent for "beginning of line" is the carat character ^, so to remove the *leading* 11 characters you'd want

```
rename 's/^.{11}//' *
```BTW if you add a -v switch (option) to rename you can confirm what it's doing

regex is always a learning experience for me - nice to see someone who likes to get under the hood with this stuff, good luck

thank you. i wasnt to far off then. lol
i just found regexxer in the repository. looks like a good front end for err. regexing.
also one last thing. how can i edit the contents of a file using regexing, rather than the contents of a directory?
oh and the *

---

### Post by Vaphell on 2012-05-13
* is a commandline symbol for 'any string including zero length' which means that it matches every file/dir in current directory
command line supports wildcards which are like regular expressions but simplified

sed tool works with the same s/pattern/replacement/ expressions, so if you get the idea of them, you are pretty much good to go

```
sed 's/something/something else/g' *.txt
```
g at the end = all occurences, because by default only first occurence in a line is replaced

by default sed prints the result in terminal without making any changes. *sed -i* is used to make changes in place, but it's risky. Regular expressions often have edge cases the user that has not foreseen and *-i* would make permanent undesirable changes to the source data. It's better to test extensively without *-i* and apply it later or use redirection of output which preserves the original
```
sed .... input_file > output_file
```

sed works with plain text only though, if you want some regular expression magic in case of document formats and such, you need to check if the software producing given file format supports search and replace based on regexes, eg. Open/Libre Office do.

---

### Post by billyseth on 2012-05-13
> **spiritech said:**
> thank you i will have a read through. i am trying to learn a little bit of bash as well. looks like all these things can be used together when writing scripts.

true it works well in bash scripts, and most programming languages in general provide some sort of regex use

---

