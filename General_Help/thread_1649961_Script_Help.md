---
title: "Script Help"
date: 2010-12-20
forum: General Help
---

### Post by rickcjmac on 2010-12-20
I wrote a very simple script to compile a Tex document and open the resulting PDF output file. The problem I have is that every now and then there are multiple PDF files in the same directory. For example if I have a file called test.tex I run my script and it compiles the test.tex and creates a file called test.pdf If there are only one tex and pdf file in this folder there is no problem. If there is also a 1.pdf in this folder the test.tex will compile and 1.pdf will open.  

My question is: is there a way to open the exact pdf file that was created by the .tex file?

My script file is this:

#!/bin/sh
pdflatex *.tex
gnome-open *.pdf

Thanks for the help :)

---

### Post by iponeverything on 2010-12-20
```
gnome-open `pdflatex *.tex`
```

---

### Post by rickcjmac on 2010-12-25
Thank you for your reply. Unfortunately

> gnome-open `pdflatex *.tex`

This threw back an error:


Error showing url: Error stating file '.../pdflatex *.tex': No such file or directory

---

### Post by iponeverything on 2010-12-26
ok, I'll give it another shot:

```

#!/bin/sh
pdflatex *.tex
ls -tr *.pdf |tail -1 |awk '{print "gnome-open "$1}'|sh

```

---

### Post by rickcjmac on 2010-12-26
That is perfect! It does exactly what I need it to do. Thank you very much for helping me out :) 

About the code, I understand everything but the |sh at the end. What does that do?

The answer to the last question might answer this one, but why does this work in a shell script, and when I type it into the terminal directly, but not in an alias? My alias is:

```
alias tex='pdflatex *.tex
ls -tr *.pdf |tail -1 |awk '{print "gnome-open "$1}'|sh
```'

and this is what the terminal says when I open a new window:

> bash: alias: gnome-open }|sh: not found

Thank you again for fixing this for me. This is exactly what I needed!:)

---

### Post by iponeverything on 2010-12-27
The command is built by awk with the argument supplied by ls and then it  is piped to sh to be interpreted.  Without the pipe to sh at the end you would only see the command. 

I think that the reason that the alias does not work is because you need to escape some of the special characters.

---

