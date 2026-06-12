---
title: "how to get latex macros (getlatex)?"
date: 2006-05-11
forum: General Help
---

### Post by amerikkanu on 2006-05-11
hey folks,
I'm trying to get latex macros that aren't in teTeX or available through apt-get (as far as I can see) using the "getlatex" app at [http://biostat.mc.vanderbilt.edu/twiki/bin/view/Main/DocProcess]("http://biostat.mc.vanderbilt.edu/twiki/bin/view/Main/DocProcess") but can't get it to work.  The instructions at that site read:

 ******************
Adding a non-included style macro such as ctable or multibib to a Linux LaTeX installation:
    * Put getlatex in /usr/local/bin and set it to be executable
    * Run it, as root, using e.g. su -c "getlatex ctable"
    * This creates a new directory in the proper place in the tex installation, downloads all needed files from [http://www.tug.org](http://www.tug.org) into this new directory, runs latex on the .ins file to create the .sty file, and runs mktexlsr to update tex indexes.
******************

So I logged in as root, downloaded the file to the specified directory, changing the file format to .exe, opened applications->accessories->terminal, cut and pasted the "su" command into it and got the reply: bash: getlatex: command not found.  What to do?  Any help would be much appreciated!  Thanks.

---

### Post by nanotube on 2006-05-11
well, seems that /usr/local/bin is not in your PATH for root.
easiest way around is to use full path:
su -c "/usr/local/bin/getlatex ctable"
try that.

---

### Post by amerikkanu on 2006-05-11
thanks for the help!  actually, i still got a file or directory not found reply.  going back to the file, i noticed it was a shell file, so i resaved it as such and was able to run it properly with help from your link to the guide on installing software.  thanks!  very useful.

---

