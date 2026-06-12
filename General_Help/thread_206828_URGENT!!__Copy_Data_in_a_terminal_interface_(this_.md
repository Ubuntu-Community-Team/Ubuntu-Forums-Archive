---
title: "URGENT!!  Copy Data in a terminal interface (this is very simple)"
date: 2006-06-30
forum: General Help
---

### Post by link141 on 2006-06-30
Please Help, I messed up xorg, and now only recovery mode (Kubuntu recovery mode in boot menu) works.  I could spend countless hours and a lot of hard work to fix this, but I don't know Linux commands, and just don't know Linux.  Also, my cousins are coming over in about 20 minutes and they want a good preview of a Linux Distribution.  I have a fast computer, and a clean install and configure should take about 15 minutes.   The only thing is, I need to copy some important data off my machine on to an external USB drive, copying my whole home folder is all I want to do before I blast a new copy onto the machine.

2 Requests:
   1.**Please** don't bother me about using the Live CD, fixing it properly, or such, I would've, but I've been too dang tired this week.
   2. Someone explain an easy (and comprehensive) way to copy my home folder onto a standard 80GB USB drive in a terminal type interface (Kubuntu recovery mode).  

The sooner, the better!  Any help **GREATLY** appreciated.  This forum hasn't let me down before!!  Thanks!

---

### Post by halfvolle melk on 2006-06-30
2. ls /media, it will show you your drive. Lest call it sda1 for now. Then
cp ~ /media/sda1

However:
1. I'll bother anyway :P . sudo dpkg-reconfigure xserver-xorg. Press enter many times, choose simple when asked, press enter some more. That might fix it.

---

### Post by arnieboy on 2006-06-30
how many times did u edit xorg.conf ?
if its just once before u borked it, then try the following:
```
sudo cp -f /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
and restart

---

### Post by link141 on 2006-06-30
Thank you for responding. 
If you could elaborate your instructions to a walkthrough that a complete Linux noob can follow, that would be awesome.  Oh, and I already did that about three or four times, this was what blew a simple problem out of proportion, 'cause some idiot (myself) thought they would edit the xorg.conf file without understanding it that well (*along* with running that command).  Also, that was my "sandbox" copy of ubuntu, and I wanted to reinstall in the future anyway. 

Thank you again for such a fast response though, you win the first-person-to-respond-to-an-idiot's-post award.

---

### Post by link141 on 2006-06-30
I noticed the fact that it told me the location of a backup file, but only after I borked it 5x over.  So for the sake of getting a copy of Kubuntu back up and running fast, and making this easy, I prefer to copy my home folder onto a USB drive, and reload the data onto the new installation.
Thank you ArnieBoy

---

### Post by halfvolle melk on 2006-06-30
```
hb@eojd:~$ ls /media
cdrom  cdrom0
hb@eojd:~$ cp ~ /media/cdrom0
cp: omitting directory `/home/hb'
```
Hmm, can't write to cdrom ... ;)

---

### Post by arnieboy on 2006-06-30
after u log in and get dropped onto console,
do the following:
```
sudo dpkg-reconfigure xserver-xorg
```
Hit OK on the defaults and when u are done, restart.

---

### Post by link141 on 2006-06-30
Thank you again for the quick response.
So, should I just type the following in the recovery-mode command prompt?
I've noticed that this USB drive always mounts as sda1, if that helps.  You have two options (of course, if you want to put up with me), 1st the prefferred, take all the info I gave you, and give me thorough, step by step instructions, or, tell me (and explain) the commands for a simple copy and paste. 

Thank you **very** much.

---

### Post by link141 on 2006-06-30
Sorry I'm typing so slow...
anyway, to clarify, I must **start** Kubuntu in recovery mode, from grub.  I will try the command that Arnie reccomended (exact command I've tried before, I think) come back, and report my status.  I will reboot back into windows if this doesn't work.  
Thanks Guys.

---

### Post by link141 on 2006-06-30
YES! It's alive! Thank you guys so much for your help!  Before when I used this command, I tried configuring it the way I wanted it, and it never occurred to me that the predetermined defaults would work.  Thanks for your persistence, and ultimately fixing my system.
Thanks.

---

### Post by halfvolle melk on 2006-06-30
Cool, good luck showing off Ubuntu :)

---

### Post by link141 on 2006-06-30
One more Question,
Another user on the forum recommended using the following options with my integrated graphics (he has a similar chip), how do I put these correctly put these into my xorg.conf file without re-borking it (sorry I keep using that word, but I now like it)? 

option "DisableIRQ"
option "EnableAGPDMA"

Thanks.

---

### Post by halfvolle melk on 2006-06-30
Dunno. That needs a new topic that says what card with what chip-set you have and a link to the method/changes you used or what you want to achieve.

---

