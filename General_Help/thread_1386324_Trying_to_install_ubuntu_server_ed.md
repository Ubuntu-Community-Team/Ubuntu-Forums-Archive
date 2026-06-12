---
title: "Trying to install ubuntu server ed"
date: 2010-01-20
forum: General Help
---

### Post by henryblowery on 2010-01-20
Hey y'all, I just installed Ubuntu 9.10 desktop edition a few days ago, and have been fooling around with it. I wanted to install the server edition and see what that's like (as I'm using this computer as a server anyway) but I've been running into trouble installing it. I put the disk with the server version in my computer, and something about updates pops up. I click run upgrade, it looks like something is happening and then I get an error message. I've uploaded screen shots for y'all to look at. What am I doing wrong?

Gray

---

### Post by lisati on 2010-01-20
Did you actually install the server edition and add a GUI?

edit (afterthought): does the CD match the version you're running?

---

### Post by henryblowery on 2010-01-20
No. I had installed the normal desktop version and later decided I wanted to check the server edition out. I currently have Ubuntu Desktop 9.10 on my computer and the CD I inserted was Ubuntu Server 9.10.

Gray

---

### Post by ks07 on 2010-01-20
To install the server edition, you need to boot from that CD you burnt. However, be aware that overwriting your desktop install means you wont have a graphical interface anymore as it is not installed by default.

---

### Post by henryblowery on 2010-01-20
I tried booting from the CD but everything comes up like normal. Obviously I was able to do so when I installed Ubuntu to start with a couple days ago. Is there anyway something could have changed? 

Gray

---

### Post by adam814 on 2010-01-20
You shouldn't be able to get a GUI from the server edition CD.  It's text-based install only.  If you're getting a GUI (and you're sure you're booting from CD) you're using a Desktop edition.

Although you *can* install a GUI in the server edition after you install it.

---

### Post by ks07 on 2010-01-20
Could you have changed the boot order in the bios? Make sure it checks the CD drive before the hard disk.

The only other reason I can think of is a bad download or CD, but I presume you checked the md5 beforehand.

EDIT: To check, you could try booting from the desktop CD which worked before. If it goes to the live cd menu, then you have a problem with the burnt server edition CD.

---

### Post by t0p on 2010-01-20
You say you could boot from CD a couple of days ago.  Unless you have specifically changed the boot device order in the BIOS, it's unlikely that has changed.  But I suppose it's worth checking.  To access BIOS settings, you need to press a particular key when you boot the computer.  On mine it's F2.  Yours may be different.

Assuming you haven't changed boot device order: you may need to press <Esc> when you boot, to get a choice of which device to boot from.  That's how it worked on an old computer of mine.  Failing that, try pressing other keys when you boot.  Hopefully you will get a menu including the option to boot from CD.

---

### Post by henryblowery on 2010-01-20
Ok, we're making progress. Hitting Esc while booting was successful, BUT after I chose the install button I got this message, "This kernel requires an x86-64 CPU, but only detected i686 CPU. Unable to boot. Please use a kernel appropriate for your CPU."

What in the Sam Hill is wrong? You'd think if my computer could handle the desktop version it could handle the server edition. Right?

Gray

---

### Post by ks07 on 2010-01-20
> **henryblowery said:**
> Ok, we're making progress. Hitting Esc while booting was successful, BUT after I chose the install button I got this message, "This kernel requires an x86-64 CPU, but only detected i686 CPU. Unable to boot. Please use a kernel appropriate for your CPU."

What in the Sam Hill is wrong? You'd think if my computer could handle the desktop version it could handle the server edition. Right?

Gray
The default download of the server edition is 64 bit. Your computer isn't capable of 64 bit, so you'll need to go back to [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server) and click "Alternative Download Options". From here pick "32 bit version" and download and burn the iso to a new CD.

---

### Post by henryblowery on 2010-01-20
Thank you Sir. I'm currently in the process of downloading the 32 bit version.

Gray

---

### Post by ks07 on 2010-01-20
> **henryblowery said:**
> Thank you Sir. I'm currently in the process of downloading the 32 bit version.

Gray
Glad to help. :) Once you've burnt it, you should be able to boot and install normally.

Anyway, I'm logging off for the night now, but if you have any more troubles I'll check back tommorow and help, unless I get beaten to it ofc.

---

### Post by henryblowery on 2010-01-21
I got it installed last night. Also got Apache2, MySQL, PHP5, and Webmin installed. Now I've got to install proftpd, get everything configured, and I should be good to go.

Gray

---

