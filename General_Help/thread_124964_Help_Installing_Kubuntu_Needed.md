---
title: "Help Installing Kubuntu Needed"
date: 2006-02-02
forum: General Help
---

### Post by anmlcrckrs on 2006-02-02
I have a Toshiba Portege 4010 933Mhz PIII-m with 256mb that I have tried to install Kubuntu on after I tested it with the live CD and there were a couple errors in the first try one was it couldn't installed the regular linux-i386 and had to install the linux-image-i386, it also couldn't install a couple extra programs I don't know which.

Well, everything boots and I get the Kubuntu load screen and then it goes to the command line of Unbuntu, I have no idea where to go from here.  Do I need to reinstall or something?  Is there something I need to setup in the command line before the desktop will boot?  

Any help appriciated!

---

### Post by [Nirvana] on 2006-02-02
What is the output of "startx" ?

---

### Post by anmlcrckrs on 2006-02-02
I'm a total noob when it comes to linux but I really like the open source community, use OpenOffice etc, and want to try my hand at linux.  Basically, please excuse me if I'm fairly lost.

Do I need to run the recovery mode to see what startx equals?  Also, what am I looking for startx to equal?  Thanks.

---

### Post by anmlcrckrs on 2006-02-02
When I run startx I get

xauth: creating new authority file /home/david/.severauth.7088
xauth: creating new authority file /home/david/.Xauthority
xauth: creating new authority file /home/david/.Xauthority

/etc/X11/xinit/xserverrc: line 2: /usr/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 2: exec: /usr/bin/X11/X: cannot execute: No such file or directory
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by [Nirvana] on 2006-02-02
What I mean by run, is when you are in the console (after logging in), type what the poster says.

try "sudo apt-get install kubuntu-desktop"

---

### Post by anmlcrckrs on 2006-02-04
Reinstalled with a new disc got it to load correctly

---

