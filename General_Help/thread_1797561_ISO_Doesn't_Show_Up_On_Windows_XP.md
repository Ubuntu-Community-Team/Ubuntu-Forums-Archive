---
title: "ISO Doesn't Show Up On Windows XP"
date: 2011-07-05
forum: General Help
---

### Post by Joshua F on 2011-07-05
I an trying to install ubuntu onto my old Windows XP computer, I have burned the **** with the ISO files on it with a Mac and also tried using Windows 7, they have the files when I load them on those, but when I go to put the disk in my Windows XP computer it say's the disk is blank. I reboot my computer, and it doesn't try to install anything.

---

### Post by An Sanct on 2011-07-05
Did you burn the ISO directly or did you use some special "tool->burn image" option?

I can't be more specific, you did not provide us with info about the software you used...

---

### Post by nzjethro on 2011-07-05
What programme have you been using to burn your .iso? I'd suggest ImgBurn or InfraRecorder. Burning the .iso is critical to producing a bootable Ubuntu CD. You could also check out Unetbootin to create a Live USB, as this will save CDs, and also run faster.

---

### Post by in-dust-rial on 2011-07-05
yeah, 
what files are exactly on the CD?

i think your system does not say the CD is 'BLANC'. more precisely it should say 'no bootable CD' or something.

good luck

---

### Post by Joshua F on 2011-07-05
I use the one that Windows 7 comes with, then I tried the one on the Mac using Disk Utility, and did what it told me to do in the little tutorial in the download section. I'll try one of those programs you suggested, and reply when I have it burned, and tried putting the disk in my Windows XP.

---

### Post by Joshua F on 2011-07-05
> **in-dust-rial said:**
> yeah, 
what files are exactly on the CD?

i think your system does not say the CD is 'BLANC'. more precisely it should say 'no bootable CD' or something.

good luck

> **nzjethro said:**
> What programme have you been using to burn your .iso? I'd suggest ImgBurn or InfraRecorder. Burning the .iso is critical to producing a bootable Ubuntu CD. You could also check out Unetbootin to create a Live USB, as this will save CDs, and also run faster.

Installed ImgBurn onto my Windows 7 computer, and used it to burn the new disk, still isn't wanting to work. It still says the disk has 0 out of 0 bytes left.

---

### Post by in-dust-rial on 2011-07-05
hey,
this is confusing(!) since it contradicts the first post. 
so there is an issue with burning CDs?
then it would be probably an issue under windows/mac?
and if it is in both then it is maybe even the hardware?

try USB stick. the tool is so FRIENDLY!
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by Joshua F on 2011-07-05
> **in-dust-rial said:**
> hey,
this is confusing(!) since it contradicts the first post. 
so there is an issue with burning CDs?
then it would be probably an issue under windows/mac?
and if it is in both then it is maybe even the hardware?

try USB stick. the tool is so FRIENDLY!
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Seems to me the CD's burn correctly, but when I put the CD into my Windows XP computer it shows the disk as blank, and says 0 out of 0 bytes left on the disk. I've tried burning it 3 different ways, Windows 7's Default Disk Burner, Mac OS's Disk Utility, and also a program called ImgBurn. Do you think using a flash drive would have any difference?

---

### Post by An Sanct on 2011-07-05
> **Joshua F said:**
> ...It still says the disk has 0 out of 0 bytes left.

After the disk is burned, it has 0 bytes left, that is normal, it is full.

If you burned the ISO this way (image...)
[IMG]http://www.imgburn.com/images/screenshot_write.png[/IMG]

Then the image is burned okay and ready to boot from :)

---

### Post by Joshua F on 2011-07-05
> **An Sanct said:**
> After the disk is burned, it has 0 bytes left, that is normal, it is full.

If you burned the ISO this way (image...)
[IMG]http://www.imgburn.com/images/screenshot_write.png[/IMG]

Then the image is burned okay and ready to boot from :)

That's exactly how I did it, I'll re-try it one more time, though.

---

### Post by Joshua F on 2011-07-05
Here's a picture of it.

Edit: Uploaded wrong pictures, he's the newer one.

[IMG]http://img194.imageshack.us/img194/3416/unledesf.png[/IMG]

---

### Post by An Sanct on 2011-07-05
hm ... Why would you be using a **server 32bit** build?????

---

### Post by Joshua F on 2011-07-05
> **An Sanct said:**
> hm ... Why would you be using a **server 32bit** build?????

Friend told me to since my XP is 32bit,

---

### Post by An Sanct on 2011-07-05
Okay, that explains 32bit ... that is okay, but why the server and not the desktop? (did I miss something? Are you trying to build a server?)

---

### Post by Joshua F on 2011-07-05
> **An Sanct said:**
> Okay, that explains 32bit ... that is okay, but why the server and not the desktop? (did I miss something? Are you trying to build a server?)

Yes, I'm trying to replace my Windows XP OS with Linux, which I know will cause me to lose all of my files, but that computer isn't ever used, so I decided to try to make it into a server. I just can't seem to get it to recognize the CD correctly, and see it has files on it, and then boot from the CD.

---

### Post by Jagoly on 2011-07-05
Ok

---

### Post by Jagoly on 2011-07-05
> **Joshua F said:**
> Yes, I'm trying to replace my Windows XP OS with Linux, which I know will cause me to lose all of my files, but that computer isn't ever used, so I decided to try to make it into a server. I just can't seem to get it to recognize the CD correctly, and see it has files on it, and then boot from the CD.

What kind of server?

---

### Post by Joshua F on 2011-07-05
> **Jagoly said:**
> What kind of server?

Web server(Apache, MySQL, FTP, etc.)

---

### Post by Jagoly on 2011-07-05
Have you got a domain name and static IP?

I Just built a server myself last week, actually.
well, it's a work in progress.

---

### Post by An Sanct on 2011-07-05
> **Jagoly said:**
> Ok
:) ?

Well, you can use the desktop edition for a small networking server with PHP, file sharing and SAMBA support, desktop also provides a normal user interface, while server is meant to be "headless", so no monitor attached and purely command line (rather tough on someone who has little server experience ... IMHO ... I personally would avoid it...)

But back to the main problem.

Burn the ISO as an image. You did that and I see no problems here... maybe the optical drive is not functioning (?)

OR use [unetbootin ]("http://unetbootin.sourceforge.net/")and make a bootable USB from the ISO, it _will_ boot faster and will not waste CDs. Installation from the Live USB runs normally, just like from the CD.

---

### Post by Jagoly on 2011-07-05
> **An Sanct said:**
> :) ?

Well, you can use the desktop edition for a small networking server with PHP, file sharing and SAMBA support, desktop also provides a normal user interface, while server is meant to be "headless", so no monitor attached and purely command line (rather tough on someone who has little server experience ... IMHO ... I personally would avoid it...)

But back to the main problem.

Burn the ISO as an image. You did that and I see no problems here... maybe the optical drive is not functioning (?)

OR use [unetbootin ]("http://unetbootin.sourceforge.net/")and make a bootable USB from the ISO, it _will_ boot faster and will not waste CDs. Installation from the Live USB runs normally, just like from the CD.

did you see my post before I edited it:oops:

---

### Post by An Sanct on 2011-07-05
Web server(Apache, MySQL, FTP, etc.) is all bundled in [LAMP]("http://www.techtickle.com/install-lamp-ubuntu-maverick-lucid-easy.html") and [FTPServer]("https://help.ubuntu.com/community/FtpServer")... (both run without a problem on the desktop edition)

---

### Post by Jagoly on 2011-07-05
Ubuntu server really isn't hard to set up; install, choose options with tasksel; stick webpage in apache's directory. I haven't set up a domain or static ip yet, though. But a gui wouldn't make that any easier. Mine is for my dad's business, it also is acting as a raid 1 file server with samba.

PS: OP's is a laptop, so it has a screen.

---

### Post by An Sanct on 2011-07-05
> **Jagoly said:**
> Ubuntu server really isn't hard to set up; install, choose options with tasksel; stick webpage in apache's directory. I haven't set up a domain or static ip yet, though. But a gui wouldn't make that any easier.

It actually is just one command
```
sudo apt-get install lamp-server^
```

tasksel is making things hard ...

---

### Post by Joshua F on 2011-07-05
> **An Sanct said:**
> :) ?

Well, you can use the desktop edition for a small networking server with PHP, file sharing and SAMBA support, desktop also provides a normal user interface, while server is meant to be "headless", so no monitor attached and purely command line (rather tough on someone who has little server experience ... IMHO ... I personally would avoid it...)

But back to the main problem.

Burn the ISO as an image. You did that and I see no problems here... maybe the optical drive is not functioning (?)

OR use [unetbootin ]("http://unetbootin.sourceforge.net/")and make a bootable USB from the ISO, it _will_ boot faster and will not waste CDs. Installation from the Live USB runs normally, just like from the CD.

I'll try the flash drive method later, I'm going to bad as it's almost 5:30am. Once I try it, I'll reply to this thread again with what happens.

---

### Post by Jagoly on 2011-07-05
> **An Sanct said:**
> It actually is just one command
```
sudo apt-get install lamp-server^
```

tasksel is making things hard ...

tasksel runs during the installation of ubuntu server

---

### Post by nzjethro on 2011-07-05
> OR use unetbootin and make a bootable USB from the ISO

+1. I suggested this in an earlier post, and if nothing else it will allow us to determine whether it is a hardware problem (i.e. the optical drive).

Also, try checking the MD5SUM hash value, by following [this guide,]("https://help.ubuntu.com/community/HowToMD5SUM") and using values found [here.]("https://help.ubuntu.com/community/UbuntuHashes") This will show you/us if your download was correct, and if you are indeed burning the correct and full file to the disk.

---

### Post by Joshua F on 2011-07-05
> **An Sanct said:**
> :) ?

Well, you can use the desktop edition for a small networking server with PHP, file sharing and SAMBA support, desktop also provides a normal user interface, while server is meant to be "headless", so no monitor attached and purely command line (rather tough on someone who has little server experience ... IMHO ... I personally would avoid it...)

But back to the main problem.

Burn the ISO as an image. You did that and I see no problems here... maybe the optical drive is not functioning (?)

OR use [unetbootin ]("http://unetbootin.sourceforge.net/")and make a bootable USB from the ISO, it _will_ boot faster and will not waste CDs. Installation from the Live USB runs normally, just like from the CD.
There's 4 options on my computer to boot from.
USB-FDD
USB-ZIP
USB-CDROM
USB-HDD

Tried them all, and it still is trying to load Windows.

---

### Post by nzjethro on 2011-07-05
Did you check the MD5SUM value as I suggested in a previous post?

---

### Post by Joshua F on 2011-07-05
> **nzjethro said:**
> Did you check the MD5SUM value as I suggested in a previous post?
Yes, they're the same.

---

