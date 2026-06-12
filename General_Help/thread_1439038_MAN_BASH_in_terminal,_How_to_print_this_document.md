---
title: "MAN BASH in terminal, How to print this document?"
date: 2010-03-25
forum: General Help
---

### Post by Young God on 2010-03-25
Hello Linux Community,

Here's my problem. I have recently discovered the command "man bash" in the terminal window which brings up the manual for bash. but I would like to print this manual what command would I use to print it from the terminal? What command would I use to copy it from the terminal and then paste it in OpenOffice Word Proccesor for editing and printing? and if the manual is accessible through the terminal that means there must be a document on my file system that contains the bash manual, which I can just go to and print from, where is this document/file?

Young God
Linux Fanatic
Web Developer

---

### Post by texaswriter on 2010-03-25
If you have a printer configured... 

```
man bash|lpr OR man bash>lpr.txt  than lpr lpr.txt
```

---

### Post by spiderbatdad on 2010-03-25
There are a few ways to redirect terminal output to text file and the like, and of course you can copy paste from the gnome terminal. To print directly from the terminal try this:
```
man bash | lpr
```

---

### Post by blur xc on 2010-03-25
> **spiderbatdad said:**
> There are a few ways to redirect terminal output to text file and the like, and of course you can copy paste from the gnome terminal. To print directly from the terminal try this:
```
man bash | lpr
```

That's fancy- but I have a question - are there any formatting options for lpr?  I read the man pages and didn't see anything.  The default font is kind of bit, wraps text to the next line when it'd look better if it didn't, and lines print off the bottom of the page...

It's still cool though...

B<

---

### Post by quadproc on 2010-03-25
> **blur xc said:**
> That's fancy- but I have a question - are there any formatting options for lpr?  I read the man pages and didn't see anything.  The default font is kind of bit, wraps text to the next line when it'd look better if it didn't, and lines print off the bottom of the page...

It's still cool though...

B<
I don't think that you really want to direct the manual to lpr because that doesn't allow any editing.  What you can do is 
```
man bash >Desktop/bashpages
```
then invoke your editor on Desktop/bashpages and work over the text as desired, then use the editor to print what you want.  When you are finished, you can remove the bashpages file or perhaps keep it for future use.

quadproc

---

### Post by quadproc on 2010-03-25
Sorry, I should have included this with the above: you might also be interested in the "info" command.  It produces a document similar to man.

quadproc

---

### Post by apmcd47 on 2010-03-25
> **blur xc said:**
> That's fancy- but I have a question - are there any formatting options for lpr?  I read the man pages and didn't see anything.  The default font is kind of bit, wraps text to the next line when it'd look better if it didn't, and lines print off the bottom of the page...

It's still cool though...

B<
Doing that gives you the terminal version of the man page on the printer. Use
```
man **-t** bash | lpr
```
to give you a proper typeset man page.

Check the man page for man. Alternatively find the source code for the bash man page (probably /usr/share/man/man1/bash.1) and type ```
groff -man bash.1
``` but check the groff man page first.

Andrew

---

### Post by apmcd47 on 2010-03-25
> **quadproc said:**
> I don't think that you really want to direct the manual to lpr because that doesn't allow any editing.  What you can do is 
```
man bash >Desktop/bashpages
```
then invoke your editor on Desktop/bashpages and work over the text as desired, then use the editor to print what you want.  When you are finished, you can remove the bashpages file or perhaps keep it for future use.

quadproc

Alternatively use tkman - if it's not in the repository just google for it. tkman is a visual display for man pages. Also tkinfo for info. I can actually navigate info pages using tkinfo.

Andrew

---

### Post by Young God on 2010-03-25
Thankx so much everyone, all of them worked. Apmcd I used your technique and got it right on my desktop and opened it in GEdit. Great stuff.

---

### Post by blur xc on 2010-03-26
> **apmcd47 said:**
> Doing that gives you the terminal version of the man page on the printer. Use
```
man **-t** bash | lpr
```to give you a proper typeset man page.

Check the man page for man. Alternatively find the source code for the bash man page (probably /usr/share/man/man1/bash.1) and type ```
groff -man bash.1
``` but check the groff man page first.

Andrew

Sweet- thanks for the info!

BM

---

### Post by psusi on 2010-03-26
Man formats the manual pages to look good on your terminal.  If you pipe the output, it will not look right on a terminal of a different size, or on paper, unless your current terminal window just happens to be the right size.  According to man man, you can pass man -Tdvi to have it output in device independent format, then pipe that to divps to format it into postscript for nice printing.

---

