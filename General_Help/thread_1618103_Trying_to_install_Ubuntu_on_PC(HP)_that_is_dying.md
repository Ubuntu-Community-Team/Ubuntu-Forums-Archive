---
title: "Trying to install Ubuntu on PC(HP) that is dying"
date: 2010-11-10
forum: General Help
---

### Post by mickholt on 2010-11-10
I am trying to salvage the contents of my HD. I have tried to install Ubuntu from a CD (I created) and keep getting the error "No DEFAULT or UI configuration directive found!" 
 
 
My OS is Vista Home.
 
Any help will be appreciated. I am kind of a noob, so type slow. THX
 
MDH

---

### Post by Hippytaff on 2010-11-10
> **mickholt said:**
> I am trying to salvage the contents of my HD. I have tried to install Ubuntu from a CD (I created) and keep getting the error "No DEFAULT or UI configuration directive found!" 
 
 
My OS is Vista Home.
 
Any help will be appreciated. I am kind of a noob, so type slow. THX
 
MDH
 
Has Vista died? if not boot into vista and backup your HD, or you should be able to access your windows files from the liveCD environment
 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

---

### Post by ironic.demise on 2010-11-10
Download a lubuntu live cd.
Lubuntu needs less system resources and the live cd will have a gui.

---

### Post by coffeecat on 2010-11-10
> **mickholt said:**
> I am trying to salvage the contents of my HD.

Are you simply trying to backup your personal files from your Vista C: partition? If so, you don't need to install Ubuntu. You can access the Vista partition from the live CD session from the Places menu. If that machine is capable of running Vista, you won't need a light desktop such as Lubuntu - the Ubuntu CD will be fine.

Is it the machine, the hard drive or Vista that is dying? Knowing which might help in deciding what is best to do.

---

### Post by mickholt on 2010-11-13
OK, VISTA boots but I cannot DO anything once it loads. Most days I get an error that says the "system tray" has stopped working (or something to that effect). But today no error messages unless I try to open a program. Files are opening, slowly, and I was able to move something from my DT to a folder, but now it's frozen. It's done nothing for 5 minutes. Should I take it somewhere or just sacrifice my files and reformat the HD?

---

### Post by coffeecat on 2010-11-13
> **mickholt said:**
> Should I take it somewhere or just sacrifice my files and reformat the HD?

Oh dear. Hippytaff and I have both already suggested what you can do. Hippytaff even gave you a howto link. Boot up from the live Ubuntu CD (do **not** install) and backup your files. It's very easy. In fact it's far easier now than in the link. With recent versions of Ubuntu you simply go into the Places menu, find your Vista C: partition and click on it. Voilà, a file browser opens from which you can copy files onto a USB drive.

---

### Post by efflandt on 2010-11-13
I don't have Vista, but if it is like Win7 to to Computer, right click on your hard drive, go to Tools, and check the boxes to check your hard drive.  Then click OK when it says it cannot do that until you reboot.  Then reboot into Windows and let it do its thing.  If that does not help, maybe you have bad sectors or a virus that corrupted your drive.

Otherwise, if you run the Ubuntu CD live, and can mount your Vista partition using Places, you could copy files to a USB device.  But if it does not mount, you may need to use testdisk to try to recover what you can.

I was trying to help someone with a failing hardrive once (WinXP refused to even boot into Safe Mode to preserve remaining data).  I could only copy some files from it with Ubuntu before the cp process hung.  When I put it in a USB enclosure neither Windows nor Linux could mount it (although, it showed up in **sudo fdisk -l**).  I let it sit for a few weeks and tried it again, and when I connected USB to an Ubuntu computer, it auto mounted and I was able to copy most of the user's files from it.

---

