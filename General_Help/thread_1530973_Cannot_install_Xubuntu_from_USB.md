---
title: "Cannot install Xubuntu from USB"
date: 2010-07-14
forum: General Help
---

### Post by linuxyogi on 2010-07-14
Hi,
I have an old PC with the following specs: 

Celeron D 2.13 Ghz , Ram = 256+128 Mb, HDD = 40Gb (PATA)

Recently I decided to bring this PC to a working condition.

Everything is working fine excepting the DVD Rom drive. It can hardly read any disc & also has a load/eject problem. So I decided to install Xubuntu via an USB Pen drive.

I downloaded Xubuntu 10.04 (32bit).

Created a USB startup disc using Lucid's Startup Disc Creator tool.

The disc ceation process went fine.

I was able to boot with the pen drive too.

Here is what happens next ---------

1. I select English.
2. Install Xubuntu

Then the screen becomes completely dark, a small cursor blinks at the top left corner of the screen & then it remain like dark forever.

I have tried the options "Try Xubuntu without installing" & Check Disc for errors".

The  "Try Xubuntu without installing" option has the same results as the installation option & "Check Disc for errors" option ends with the message "press any key to restart".

What's wrong ? Did I miss something? Please help.

Note: I created & tested the usb disk using my new PC.

---

### Post by bobcollard on 2010-07-14
Try to burn the ISO using unetbooten, it seems to work more efficiently and without the problems you are having.

---

### Post by linuxyogi on 2010-07-14
> **bobcollard said:**
> Try to burn the ISO using unetbooten, it seems to work more efficiently and without the problems you are having.

I just did that, it worked when I tested it on my new PC but now there is another problem.

Please visit [http://ubuntuforums.org/showthread.php?p=9590440#post9590440](http://ubuntuforums.org/showthread.php?p=9590440#post9590440)

Thanks a lot for trying to help.

---

### Post by HenneBaby02 on 2010-07-14
I had that same problem on my Dell Dimension 2350 (that im using now) with Xubuntu installing.


But i got it to work if u install regular Ubuntu then after it fully installs and your in gnome.
Open Terminal and type sudo apt-get install xubuntu-desktop

Then log out or reboot (whichever) and select i believe XFDE ? or something of that nature (only tried it once) and you`ll be in Xubuntu. Hope it helps.

EDIT: sorry i can't remember the name.. So maybe after you install ubuntu keep track of the desktops u can log into b4 installing Xubuntu. Then the new one should be it.

---

### Post by linuxyogi on 2010-07-14
> **HenneBaby02 said:**
> I had that same problem on my Dell Dimension 2350 (that im using now) with Xubuntu installing.


But i got it to work if u install regular Ubuntu then after it fully installs and your in gnome.
Open Terminal and type sudo apt-get install xubuntu-desktop

Then log out or reboot (whichever) and select i believe XFDE ? or something of that nature (only tried it once) and you`ll be in Xubuntu. Hope it helps.

EDIT: sorry i can't remember the name.. So maybe after you install ubuntu keep track of the desktops u can log into b4 installing Xubuntu. Then the new one should be it.

Its XFCE.

I won't be able to install ubuntu & this is why

[http://ubuntuforums.org/showthread.php?p=9590440#post9590440](http://ubuntuforums.org/showthread.php?p=9590440#post9590440)

---

### Post by linuxyogi on 2010-07-30
> **HenneBaby02 said:**
> I had that same problem on my Dell Dimension 2350 (that im using now) with Xubuntu installing. 

**_THIS IS THE SOLUTION_**

Enter bios, find "memory hole", disable it.

---

