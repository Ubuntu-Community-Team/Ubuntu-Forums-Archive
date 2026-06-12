---
title: "Text-processing commands?"
date: 2009-11-23
forum: General Help
---

### Post by t0p on 2009-11-23
I've had difficulty figuring out how to do a text-processing task, I hope someone here can help.

When you run the command

```
dpkg --get-selections > file
```you get a text file looking something like this excerpt:

> 
heirloom-mailx                    install
hicolor-icon-theme                install
hostname                    install
hotkey-setup                    install
hplip                        deinstall
html2text                    install
human-icon-theme                install
That is, a text file consisting of 2 columns: column 1 is an alphabetical list of software packages, and column 2 says "install" if the package is installed and "deinstalled" if the package is not installed (any more).

**EDIT: For some reason, pasting the list into this forum has messed up the formatting.  In the original, each column in the list is nicely formatted to a straight margin.**

What I want is a list of all the installed packages, without the "install" bit.  (Eventually I want to use this list in an apt-get command, so when I install Karmic I can get all these packages installed.)

Can someone advise me how to turn this list into the list I want?

---

### Post by CaKiwi on 2009-11-23
Try awk

```
dpkg --get-selections | awk '$2=="install"{print $1}' > file
```

I'm not near a linux system, you may need to use gawk rather than awk

---

### Post by alphaniner on 2009-11-23
**dpkg --get-selections | cut -f1** worked for me.

---

### Post by t0p on 2009-11-23
**CaKiwi:**  Thanks, that's just what I wanted.

**alphaniner:** Using your command resulted in a list of all the packages that appeared in my original file, including the ones marked "deinstall"; I only wanted those marked "install" to appear.  

But thanks anyway!

---

### Post by alphaniner on 2009-11-23
Oy, sorry.  I thought you just wanted everything in the first column.

In that case another option would be **dpkg --get-selections | grep -v deinstall**.  But awk may be more efficient.

---

### Post by t0p on 2009-11-23
> **alphaniner said:**
> Oy, sorry.  I thought you just wanted everything in the first column.

In that case another option would be **dpkg --get-selections | grep -v deinstall**.  But awk may be more efficient.

Thanks: but yeah, I think I'll stick with awk.

Tell you what, I'm having some trouble getting my head around the syntax of awk.  Hope it clicks soon!

---

### Post by CaKiwi on 2009-11-23
The Twitter edition of the Awk manual

Awk takes each line of input and breaks it into fields delimited by white space (by default). The 1st field is $1, the 2nd $2, etc. Each Awk statement consists of a pattern followed by an action in {}. If the pattern is true, the action is executed.

 In our case, the pattern is $2=="install" and the action is {print $1}. Check out [http://www.gnu.org/manual/gawk/gawk.html](http://www.gnu.org/manual/gawk/gawk.html) for more info

Ok, ok, it's the 2 tweet manual.

---

