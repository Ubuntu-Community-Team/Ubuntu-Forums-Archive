---
title: "How to make a launcher??"
date: 2011-12-08
forum: General Help
---

### Post by GTO69 on 2011-12-08
Hi everybody,
I just installed matlab r2010a in my 11.10 ubuntu. The only way to run it is to go to */usr/local/mathlab/bin* as *root* and run *matlab.sh*.
I managed to make an icon of it at */usr/share/applications/* and it also shows up at the applications menu, but when i start it, it says  that it can't launch matlab because "Failed to execute child process "matlab" (No such file or directory)". Please can anybody help me to fix this problem??

---

### Post by zero2xiii on 2011-12-08
Hay,

Make a link, or:

Rightclick
Create launcer
Name: Matlab
Command: gksudo /usr/local/mathlab/bin/matlab.sh

This can be done anywhere, even on the desktop if you wish

Cherz

---

### Post by bluexrider on 2011-12-08
> **zero2xiii said:**
> Hay,

Make a link, or:

Rightclick
Create launcer
Name: Matlab
Command: gksudo /usr/local/mathlab/bin/matlab.sh

This can be done anywhere, even on the desktop if you wish

Cherz

also make sure the permissions of matlab.sh are executable

---

### Post by GTO69 on 2011-12-08
Thanks for your advices.
I tried to do as you said, also changed it's permisions, but it still doesn't work.
I noticed that i can't open it even from terminal.The only way that i can, is to go from GUI to usr/local/mathlab/bin, double-click the matlab file and from the window that apears, to choose the "run from terminal" option. If i choose just "run" the program starts loading and it closes after the a second

---

### Post by bluexrider on 2011-12-08
> **GTO69 said:**
> Thanks for your advices.
I tried to do as you said, also changed it's permisions, but it still doesn't work.
I noticed that i can't open it even from terminal.The only way that i can, is to go from GUI to usr/local/mathlab/bin, double-click the matlab file and from the window that apears, to choose the "run from terminal" option. If i choose just "run" the program starts loading and it closes after the a second
may not have installed all the dependencies.  Is there a help file or a web link you can check

---

### Post by zero2xiii on 2011-12-08
Hay,

Does it load correctly when you "open in terminal"? Is there any output in the terminal? Might get a warning or error to point you in the correct direction.

This is a strange issue..

---

### Post by GTO69 on 2011-12-08
it might be... I removed it and I'm trying to install it again

---

### Post by zero2xiii on 2011-12-08
Hay,

There is a process to getting matlab to work see the following:
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
[https://help.ubuntu.com/community/MATLAB/R2010a](https://help.ubuntu.com/community/MATLAB/R2010a)
[http://wirelesscafe.wordpress.com/2009/06/04/how-to-install-matlab-and-how-to-make-it-work-on-linux/](http://wirelesscafe.wordpress.com/2009/06/04/how-to-install-matlab-and-how-to-make-it-work-on-linux/)

Good luck

EDIT:
Looking at the first link, matlab r2010a wont run on ubuntu 11.10, as even r2011a is to old.

---

### Post by GTO69 on 2011-12-08
Damn,,,I have read these links a couple of times today, and I've been missing the most important part...Now I think that upgrading was a mistake :( i should have kept my old nice 10.10...Is there any chance for me now to use matlab and my 11.10 at the same time???

---

### Post by gennatolls on 2011-12-08
I've installed Matlab a couple times now (10.04,11.04, and 11.10). I like to do a fresh install. But try this [http://ubuntuforums.org/showthread.php?t=1416028](http://ubuntuforums.org/showthread.php?t=1416028) 

Note the second post by daliakopoulos, that fixed my problem when I had the same error message your getting.

---

### Post by gennatolls on 2011-12-08
> **zero2xiii said:**
> Hay,

There is a process to getting matlab to work see the following:
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
[https://help.ubuntu.com/community/MATLAB/R2010a](https://help.ubuntu.com/community/MATLAB/R2010a)
[http://wirelesscafe.wordpress.com/2009/06/04/how-to-install-matlab-and-how-to-make-it-work-on-linux/](http://wirelesscafe.wordpress.com/2009/06/04/how-to-install-matlab-and-how-to-make-it-work-on-linux/)

Good luck

EDIT:
Looking at the first link, matlab r2010a wont run on ubuntu 11.10, as even r2011a is to old.

I'm running matlab r2010a on 64 bit 11.10. I [this]("https://help.ubuntu.com/community/MATLAB/R2010a") straying from it occasionally where I found some typo's or contradicting information, then I edited the launcher file to match my previous post.

---

### Post by GTO69 on 2011-12-10
Thank's. You helped me a lot. I struggled a little modifying the launcher, because it had to be run from terminal in order to work, but now it's everything Ok. I have a launcher in my desktop wich opens it immediately, with a double-click. Thank you and everyone else who commented here and helped me solve this.

---

