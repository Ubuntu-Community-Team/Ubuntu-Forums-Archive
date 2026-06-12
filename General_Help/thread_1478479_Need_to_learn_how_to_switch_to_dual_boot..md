---
title: "Need to learn how to switch to dual boot."
date: 2010-05-09
forum: General Help
---

### Post by hedgeberg on 2010-05-09
Recently, just installed 10.04. Seems to work well, but I think I did something to the BIOS or the boot loader. I used to boot directly into windows. What I have now is a boot directly into ubuntu which gives me a list of the following options (abbreviated): 
Ubuntu 10.04
ubuntu 10.04 recovery mode
[Something goes here, I think its memory scan]
Microsoft windows recovery sector (On Sda/sd3) [this was my OS partition up until installation ]
Windows XP embedded [I don't even use this. i think its like a 2 gig parition to install XP on]
Now then, I installed to a seperate hard drive (seagate 1 tb windows), using manual install, and selected 3 partitions: 1 ext3 mounted on /, 1 ext3 mounted on /home, and 1 swap partition. 
currently, both ubuntu and windows run fine (I load windows from the recovery sector, no data lost since I installed ubuntu to the external hard drive), but this menu relies on data on the hard drive. When I disconnect the hard drive and then boot, it goes into a "grub recovery" command list. I need to edit the grub so that it gives me the option to boot into windows or into ubuntu, and if I choose ubuntu it gives me this option. The reason it matters is that I am using a laptop and I can't start the computer unless it is connected to the external drive. So, can I edit the grub (or the microsoft boot loader) to dual boot?

---

### Post by nitstorm on 2010-05-09
**Maybe** this could help you?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

And once the MBR is present you can write Grub2 to it by following this link:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by bcbc on 2010-05-09
You installed the grub2 bootloader to the internal hard drive MBR, so it looks on the external for the grub menu.

What you need to do is restore the windows bootloader on the internal, and then when you have the external plugged in, manually select to boot from the external (e.g. on my laptop if I hit F12 while BIOS loads, I can select 'boot from usb device').

So check whether you can boot from the external as above and confirm it boots correctly. If not, you may need to install grub to the MBR of the external... boot ubuntu from the internal and run the following from terminal. 
```
sudo grub-install /dev/sdb
```

Then install the windows boot loader to the internal MBR (using windows install/repair dvd) or alternatively you can install the lilo bootloader - it does the same thing and you can do it right from ubuntu:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

For the above - make sure your internal drive is /dev/sda and the external is /dev/sdb before running the commands:
```
sudo fdisk -l
```

---

### Post by techunit on 2010-05-09
What you are seeing is the grub loader...

You need to install the GRUB loader to the hard drive.
 There is ton of info on doing this but... I haven't found much that I have ever had to use.

---

### Post by hedgeberg on 2010-05-09
I tried to load directly from the external hard disk before i did anything, just to check if it really was loading from the Hard disk. tried, and it said it was "Missing NTLDR (at least i think that was it), press Ctrl + Alt + Del to restart". did, and booted into windows with the grub. windows immediately ran CHKDSK. dunno why. I think that some components of the grub are on the internal hard drive, some on the external. So, can i move all of the grub to the external drive? also, what is NTLDR?

---

### Post by solwic on 2010-05-09
> **hedgeberg said:**
> I tried to load directly from the external hard disk before i did anything, just to check if it really was loading from the Hard disk. tried, and it said it was "Missing NTLDR (at least i think that was it), press Ctrl + Alt + Del to restart". did, and booted into windows with the grub. windows immediately ran CHKDSK. dunno why. I think that some components of the grub are on the internal hard drive, some on the external. So, can i move all of the grub to the external drive? also, what is NTLDR?

NTLDR is, if I'm not mistaken, the Windows equivalent of Grub.  It rests in the MBR and is called up to load Windows when you boot up the machine.

EDIT:  I should add that if you have a Windows disk you can use it to go into recovery mode and, at the C: prompt, run FIXMBR to reinstall NTLDR to the MBR of the drive.

EDIT2:  You should be able to move Grub to the external drive.  You should have been able to choose that at the last screen in the Ubuntu install sequence before the install itself starts.  There's an "advanced" button or something, I believe.  

Also, it's possible to edit boot.ini in Windows and add a line for Ubuntu.  I'm not sure how it would work with an external USB drive, but it's something to look into.

---

### Post by bcbc on 2010-05-09
Post the output of the [bootinfoscript]("bootinfoscript.sourceforge.net").

---

### Post by hedgeberg on 2010-05-12
bootinfoscript had some issues, so ill have to get back to  you on that. However, i did have a realization as to why I couldn't boot to my external hard drive. I can make it possible to boot to the external hard drive, so all I am concerned with now is restoring the windows boot loader. what do i need to do for that?

EDIT: After rereading bcbc's post, I started wondering if I could reinstall the boot loader from the recovery disk without reinstalling the entire windows OS. Is it possible?

---

