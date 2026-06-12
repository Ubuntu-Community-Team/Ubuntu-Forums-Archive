---
title: "Dual boot XP &amp; Ubuntu w/ XP previously installed but boots straight to XP"
date: 2009-08-23
forum: General Help
---

### Post by tejas_ND on 2009-08-23
Hello all,

I've spent some time searching the forums for my issue but couldn't find something that helped.  So i'm posting the question.

I'm not really new to installing linux but always seem to have problems.  I run 3 sata drives(1x320gb and 2x750gb), 2 are mirrored and one is for operating systems.  I also run an AMD phenom quad core and a asus mobo.  I installed XP onto the 320gb drive a while back and left a 100gb partition for later use with a linux install.  I decided to finally get around to installing ubuntu to the 100gb partition and it went smoothly.  However, upon restart, it boots directly into XP.  There are no boot options.  I was wondering if GRUB has issues seeing sata drives or if something just didn't work during the install.  Help would be appreciated.  Thanks all.


P.S. better than last time though.  I managed to corrupt my XP partition as well last time....

---

### Post by P4man on 2009-08-23
Im guessing you installed grub on the wrong drive, or not at all?

anyway have a look at this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

WARNING: if you do that, there is fair chance windows won't be in the grub menu and so you cant boot it. If that happens, follow this (second part):

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by tejas_ND on 2009-08-23
The first guide seemed to work when i went through it using the live cd.  it only found one thing and it was labeled hd0,4 so i used that.  the setup had no errors and worked fine.  However, when i restarted there was still no grub boot menu and it booted straight to windows.  Could i have done it wrong?

EDIT:  this is what it does when i follow the instructions,

grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 

then i quit out and restart.

---

### Post by egalvan on 2009-08-23
If indeed the machine goes straight to XP, without ANY other steps,
as if XP was the ONLY OS installed,,,

then the GRUB code was not installed on the boot drive's Master Boot Record (MBR)

GRUB has no issues with SATA, or PATA, or floppies, etc.
It's all the same to GRUB.

SuperGRUB LiveCD is an excellent tool for solving boot problems.

It's not  exactly intuitive, but the on-line guides are fairly good.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

herman also has some EXCELLENT stuff on his site.
Highly recommended.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by tejas_ND on 2009-08-23
So, using SDG i can force my computer to boot into linux.  However, I don't know how to correct the grub from in linux.  I've looked at SDG's site but it's confusing and takes me in a circle.

---

### Post by P4man on 2009-08-23
ok this is a WILD guess.
Do you perhaps have an "antivirus" protection in the bios that prevents grub from rewrting your master boot record ?

---

### Post by tejas_ND on 2009-08-23
good guess but no, there is no antivirus program.  :(

---

### Post by P4man on 2009-08-23
just to be clear, its not a "program", its part of the BIOS. It can be called 'virus protection" or "boot protection" or something similar.

If thats not it.. then can you tell me the boot order in your bios? Do you have a function key you can press to boot another device ? If so, for the heck of it, can you try booting off your other harddisks ?

---

### Post by tejas_ND on 2009-08-23
yes, there is no protection turned on in my bios to stop writing to the MBR.  There is no function key either to boot another device.

My boot priority most of the time is:

Hard drive
removable
CD Rom

For now it's:

CD Rom
removable
Hard drive

So I can boot from CD.

---

### Post by P4man on 2009-08-23
I meant the boot order of the harddrives. 
Also, make sure you dont have an USB stick inserted..

---

### Post by tejas_ND on 2009-08-23
I'm not sure about the boot order of the hd's.  there is no option to change it in the bios.  there is no usb drive plugged in.  thank you for your help btw.  :)

---

### Post by tejas_ND on 2009-08-23
I got it to work.  Thanks for the help P4. :D  Turns out I kept over looking that i could indeed change my hd boot priority.  I swaped them and it came right up to grub the next restart.  thanks again for the help. :D

---

### Post by P4man on 2009-08-24
aha. Well, now you probably have your grub bootloader on one 0f the raid drives though, it cant be on the windows drive, otherwise it would never boot straight in to windows. I guess the good thing about that is that if you ever remove those drives, windows will still work heh.

---

### Post by tejas_ND on 2009-08-24
I think my issue is an old vista install.  Which means I probably won't fix it until i upgrade my entire rig again.  but, i'm happy it works for now and maybe i'll fix it one of these days that i get bored.

---

