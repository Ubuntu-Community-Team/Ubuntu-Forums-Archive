---
title: "help installing guitarpro6 ubuntu  11.10 64 bit"
date: 2012-07-29
forum: General Help
---

### Post by artofshred87 on 2012-07-29
i am trying to install guitarpro6  using this method

 sudo dpkg --force-architecture -i GuitarPro6.deb
[sudo] password for aos87: 
dpkg: error processing GuitarPro6.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 GuitarPro6.deb

what am i doing wrong

i already downloaded the getlibs-all.deb and i think they are in stalled i used gdebi and it said it was i was followinf this 

We currently do not have a 64-bit version. But you can use 32-bit wrappers to use GP6 with a 64-bit distribution.

Here's how you can run Guitar Pro 6 on a 64-bit installation:

1) Download the latest .deb from Guitar Pro's website.
2) Goto [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and install getlibs-all.deb
3) Run this in terminal

Quote:
sudo dpkg -i --force-architecture Downloads/GuitarPro6-r7840.deb

You will get some errors but ignore.

4) Run this in terminal

Quote:
getlibs /opt/GuitarPro6/GuitarPro

---

### Post by Media Boot on 2012-07-29
Is the package you are trying to install in the same directory you are executing dpkg from ?

---

### Post by artofshred87 on 2012-07-29
um im not entirley sure i am still fairly new to ubuntu can you maybe explain a little. thanks

---

### Post by Media Boot on 2012-07-29
Where did you save GuitarPro6.deb ?

---

### Post by oscarivera9 on 2012-07-29
Hi,
I wasn't aware that Guitar Pro was available for Linux but I guess it is.  I just went to the Guitar Pro website and it does show that it is Linux compatible, but I have never tried to install that program, and right now I won't go through that process because I am actually migrating from one PC to another (adding another program is the last thing I need right now).  If not for that, I would go through the installation process with you by installing it in my computer.

However, this is just a thought:  Have you looked into tuxguitar?  It's free & open source software (FOSS) which means it works great with Linux.  I actually have it installed in my Ubuntu 12.04 as well as my Windows 7 and I can testify that it is an awesome piece of software.  It does a lot of the same things that GuitarPro6 does, including opening GPx files (GuitarPro files).  In fact, I often get Guitar Pro downloads from ultimate-guitar.com and open them with tuxguitar and have no problems whatsoever.  To install it, all you have to do is open up the Ubuntu Software Center and search for tuxguitar and the rest is child's play.  The download/installation is a breeze and it takes less than 5 minutes (depending on your hardware and internet connection). You may want to check it out, all you've got to loose is a little bit of precious time, but you've got a lot to gain.

---

### Post by artofshred87 on 2012-07-31
hi srry for the late replies, i have the gp6.deb in my downloads folder, and i also have the gp cd/dvd and it has it on there also.  i do currently have tux guitar but it wont open .gpx files and most of my work is in that ext. i prefer gp more anyway, but thanks for the suggestion.

---

