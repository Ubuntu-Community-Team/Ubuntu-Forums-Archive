---
title: "command help"
date: 2011-12-03
forum: General Help
---

### Post by smasher40 on 2011-12-03
Hi i'ts me again, for the past days i've been battling with bash scripting LOL, i'm trying to learn the most i can, right now i have a doubt that i hope yall can help me



$ cut -f1 -d: /etc/passwd

i know that this command  gives me the value of the column 1 of the file passwd

then associated with this operator

$ cut -f1 -d:  /etc/passwd < teste.txt

was supposed to use this file as entry right?? but it keeps me giving the same thing, can anyone help on this matter??


thanks a  lot

---

### Post by carranty on 2011-12-03
What do you mean by "was supposed to use this file as entry right??"

If you're trying to write the output to the file teste.txt you've got your arrow the wrong way round.

```
cut -f1 -d:  /etc/passwd > teste.txt
```

should do it.

---

### Post by carranty on 2011-12-03
If however, you want to use the file teste.txt as the input, and cut out the first field you would use
```
 
cut -f1 -d: teste.txt

```And if you want to save the output of the above to a file foo.txt you would use

```
 
cut -f1 -d: teste.txt > foo.txt

```
Basically the > symbol redirects anything going to standard output to whatever location you write after it.  I'm not sure what < does, if anything.  

What are you using to learn scripting by the way?  I'm also just learning myself (from Schotts' book), always interested in new sources of information! :)

---

### Post by smasher40 on 2011-12-03
> **carranty said:**
> What do you mean by "was supposed to use this file as entry right??"

If you're trying to write the output to the file teste.txt you've got your arrow the wrong way round.

```
cut -f1 -d:  /etc/passwd > teste.txt
```

should do it.

what i was trying to say is that both commands give-me the same output, which is the first column of the passwd file, when the second command should use teste.txt as input righ???

resuming

what the output of this command should be?

cut -f1 -d: /etc/passwd < teste.txt

thanks for everything

---

### Post by smasher40 on 2011-12-03
> **carranty said:**
> If however, you want to use the file teste.txt as the input, and cut out the first field you would use
```
 
cut -f1 -d: teste.txt

```And if you want to save the output of the above to a file foo.txt you would use

```
 
cut -f1 -d: teste.txt > foo.txt

```
Basically the > symbol redirects anything going to standard output to whatever location you write after it.  I'm not sure what < does, if anything.  

What are you using to learn scripting by the way?  I'm also just learning myself (from Schotts' book), always interested in new sources of information! :)

right now i'm learning by the docs that my teacher is giving me, and as many pdf as i can find online, although some things are still hard to understand because i'm still in the beginning of the learning process.

by the way if it isn't to much hassle can you help me out in two more commands

sleep 36 ; echo "Hi There" & <-- what does this symbol does? i tried the command and it seems to output the process id also, is it that?

the other one is:

find / -mtime -1 \ ! -type -d -print

thanks a lot four your patience 

:):):):):):)

---

### Post by carranty on 2011-12-03
[QUOTE=smasher40;11510542]what i was trying to say is that both commands give-me the same output, which is the first column of the passwd file, when the second command should use teste.txt as input righ???[QUOTE]

No.  Lets take a simpler command like cat.  Cat is just program that reads text files.  We say that it takes standard input and copies it to standard output.  For example if you create a text file foo.txt you can read it using

```
cat foo.txt
```Here, the keyboard (which you used to type 'foo.txt') is the source of standard input.  If you wish to change (redirect) the source of input to a file you would write

```
cat < foo.txt
```The latter is not particularly useful, because it involves (slightly) more typing for the same result, but that is what the '<' symbol does, it redirects standard input from the keyboard to a file.  Both of the above will print the contents of foo.txt to standard output (the terminal). If you want to redirect standard output you use the > symbol. For example

```
ls 
```will list files in a folder and send the information to the terminal

```
ls > harry.txt
```will also list files in a folder, but it will be written to the file harry.txt rather than the terminal.

I hope that clears things up.  In your case your giving the cut command /etc/passwd as std input, anything following this is redundant and therefore ignored.  If you want to use teste.txt as input simply use 

```
cut -f1 -d: teste.txt
```or equivalently 

```
cut -f1 -d: < teste.txt
```

The latter line seems silly though, I don't see it used often and I'm not sure why your teacher is using it.

---

### Post by carranty on 2011-12-03
> **smasher40 said:**
> right now i'm learning by the docs that my teacher is giving me, and as many pdf as i can find online, although some things are still hard to understand because i'm still in the beginning of the learning process.

Take a look at the book by William Schotts, its free to view and I've found it very informative.

> by the way if it isn't to much hassle can you help me out in two more commands

sleep 36 ; echo "Hi There" & <-- what does this symbol does? i tried the command and it seems to output the process id also, is it that?The sleep command causes the terminal to wait 36 seconds before executing the echo command.  Without the & symbol your terminal would just hang and be unusable for the 36 seconds.  Adding the & symbol on the end of a command sends it to the 'background', so you can still do other things in your terminal while it is running.

EDIT : In fact, for it to work properly I think you'll need brackets around everything before the &
```

(sleep 36 ; echo "Hi There") &
```

> the other one is:

find / -mtime -1 \ ! -type -d -print

The find command is quite complicated (but also very versatile!). It has a good man page, you'll find what you're looking for in there.

```
man find
```

---

### Post by smasher40 on 2011-12-05
Hi me again


sorry to bother you once again :) this might be real simple but can u tell me what does this command means:

echo $$

e tried it and the output it's a number "1975", what number is that???

i'm trying to understand the whole syntax :) 

take care

---

### Post by Lars Noodén on 2011-12-05
$$ expands to the process id of the shell.  It and other speial variables are buried down in the manual page for [bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html).

---

### Post by sisco311 on 2011-12-05
EDIT: Lars Noodén beat me to it.

Prints the process ID of the shell.
See:
```
man bash | less +/"^ +Special Parameters"
```

---

### Post by smasher40 on 2011-12-05
Hi carranty

One question is there any comand to sort the information grabbed from a file???

My teatcher asked me to extract from an HTML file the Operating systems that were in a table so i did with the the following command:

[B][I]grep 'TD_WIDTH' OSs.html | tr -s '>' '#' | cut -f3 -d# | head -5 | tail -4
[/I][/B]
and the output was :

windows
MAC OS X Power PC
MAC OS X intell
Lnux

then he told me to sort that output

is there any command for that?? or it must be an argument of any other known command that i already performed in that operation.

Thanks once again for your patience

Paulo

---

### Post by sisco311 on 2011-12-06
Your teacher probably mentioned the **apropos** and **man** commands. Why don't you use them? :evil:

```
apropos -a sort file
```

As an aside note, you can't realistically parse tag-based markup languages like HTML and XML using Bash or utilities such as grep, sed or cut. If you just want to dump/render HTML, see the -dump option of links, links2, lynx and w3m or html2text or vilistextum. For parsing out pieces of data, see tidy and xmlstarlet, xmlgawk or xpath, or xslt.

---

