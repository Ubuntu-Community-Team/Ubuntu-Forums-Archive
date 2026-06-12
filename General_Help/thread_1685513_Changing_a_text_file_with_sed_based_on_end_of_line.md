---
title: "Changing a text file with sed based on end of line"
date: 2011-02-10
forum: General Help
---

### Post by evan54 on 2011-02-10
Hi,

I'm trying to add a bunch of 0s at the end of a line. The way the line is identified is that it is followed by a line which starts with "expr1"

in Vim what I do is:

s/\nexpr1/ 0 0 0 0 0 0\rexpr1/

and it works fine. I know that in ubuntu \n is what is normally used to terminate the line but whenever I do that I get a ^@ symbol so \r works fine for me. I thought I'd use this with sed but it hasn't really worked. here is what I normally write:

sed "s/\nexpr1/ 0 0 0 0 0 0\rexpr1/" infile > outfile

this doesn't do anything though which is why i'm stuck..

thanks

---

### Post by asmoore82 on 2011-02-10
This is a hard coded limitation of tools like `sed` and `grep` - they
operate 1 line at a time - so `sed` can't technically do what you want.

However, it is the ultimate triumph of the Spirit of Unix when you can achieve
successful results that the program's original authors never intended.
Especially when you do so with just the tools already available to you -
no new coding necessary.

So let's redefine the problem:
`sed` can find and replace at the beginning *or* end of lines.
`sed` cannot add to the end of 1 line based on what is at the beginning of the next line.
In other words, `sed` can never find and replace *around* a newline.

The solution is to eliminate the newlines, `sed` can find and replace practically
anything else. So, I use the `tr` command to replace newlines with carriage returns,
then `sed` does the heavy lifting, then another `tr` brings the newlines back:
```
cat *infile* | tr '\n' '\r' | sed 's/\rexpr1/ 0 0 0 0 0 0&/g' | tr '\r' '\n' > *outfile*
```
^the `g` option to `sed` is extremely necessary, because from
sed's point of view, it made all changes to 1 big long line.
without `g`, it will make only 1 change and stop

^the `&` is a little shortcut - `sed` replaces it with the original matched sequence.

Obviously, the only catch is that if the file contained any literal carriage
returns to begin with, they will be turned into newlines by the 2nd `tr`.
Such files should not naturally exist on a Unix system.

---

### Post by evan54 on 2011-02-10
awsome! thanks :D

---

### Post by Vaphell on 2011-02-10
sed can work with multiple lines, but it's ungodly annoying
there is that thing called hold buffer which can be used to glue multiple lines together. with G or H command (G = glue content of hold buffer with the content being worked on, H - inverse operation, x - swap, h - copy stuff to hold buffer to replace old value, g - get from buffer to replace current content)

for example
```
sed '=; p; H; x; s/AAA/VVV/'
``` would 1. print line number, 2 print current string 3. to the end of the buffer attach \n+current string, switch places (string goes to buffer, \n+string goes to workspace) and replace AAA and BBB in multiline string and print the result. Unfortunately it's not too intuitive to create a correct workflow with these very basic operations.
AWK seems more flexible because you can use full blown variables to store temporary values.

---

