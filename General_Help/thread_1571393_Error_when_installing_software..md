---
title: "Error when installing software."
date: 2010-09-09
forum: General Help
---

### Post by Leshinsky on 2010-09-09
I am trying to install a few programs.  One is a free dvd ripper from [http://www.free-star.org/download.php?product=free-dvd-ripper-i386.deb](http://www.free-star.org/download.php?product=free-dvd-ripper-i386.deb) and when i use the package installer to install it i get a message "error: wrong architecture 'i 386'"  can someone help me with this.

---

### Post by 0004tom on 2010-09-09
Can you post the output from 

```
uname -m
```

From the link I can only guess your trying to install a 32bit app on a 64bit machine.

You can force dpkg to install it with, from terminal

```
sudp dpkg -i --force-architecture free-dvd-ripper-i386.deb
```

---

### Post by sikander3786 on 2010-09-09
It means you are not running "i386" Ubuntu. You should be running 64-bit version so look for a download link for 64-bit.

Edit: Couldn't find a link for 64-bit on the website. Try installing as 0004tom suggested.

---

### Post by Leshinsky on 2010-09-09
I guess i do have a 64 bit version of ubuntu.  I am trying to find a program to rip the whole dvd as a whole not just title by title like the ones i found in the software center.  any ideas.  i like the free dvd ripper as stated above but cant even get it to force with the command divin above.  help please.

---

### Post by Leshinsky on 2010-09-09
Does anyone have any ideas.

---

### Post by Leshinsky on 2010-09-09
Does anyone know how to get a good dvd ripper that puts the output into a normal file.  I found a program that works but it wants to put it into a .ogv file that i have never heard of.  How do you play this file.  Also does anyone know how to get a way to watch dvds from the disk drive.  I am having problems with the other commands i have tried to use to view encripted dvds so i wont even put those commands on here and just start from scratch.

---

### Post by oldos2er on 2010-09-09
What do you mean by "normal file"? If you mean an *iso file, right-click on the DVD, choose 'Copy disc' and copy it to an image file (iso).

.ogv is Ogg Vorbis, an open source video format, which should play 'out of the box' in Ubuntu.

More info here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

