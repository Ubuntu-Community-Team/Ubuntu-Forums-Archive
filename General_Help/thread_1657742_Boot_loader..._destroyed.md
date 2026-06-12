---
title: "Boot loader... destroyed?"
date: 2011-01-01
forum: General Help
---

### Post by AbyssWolf1105 on 2011-01-01
So, I was messing around with a new 500G harddrive that I got from school.
I tried splitting it into 3 partitions:

100G - Ubuntu 10.10
100G - Fedora14
300G - Media


I got Ubuntu on no problem, this being the usual Linux machine I use.
But when I installed Fedora, not only did it make the Grub for the portable HDD go away. It also messed with my desktops grub. So now I have to have my portable HDD in to go to the Fedora boot screen, then click other OSs. Then it boots me into Windows.

Besides being aggravating because I use Windows only for gaming, and Ubuntu for everything else, I would like to be able to boot into my desktop OSs without this blasted Portable HDD plugged in.

Thank you all again

---

### Post by Whyzer on 2011-01-01
This is going to take some tinkering on your end but it's fixable. Because grub got updated when the external drive was put in it changes the boot number from within grub, without you knowing it. Same thing happens when i unplug my removable drive (which is SATA), it messes up my grub order (and it doesn't have an OS on it). Since I am in Windows right now I can't get to my ubuntu files but here's kind of what your /etc/default/grub file might look like

timeout 5 #The number of seconds GRUB should wait before booting an OS
default 0 #The entry which should be booted by default
fallback 1 #The entry which should be booted in the event of the first one failing

title  Ubuntu, 2.6.10 #A 32-bit Ubuntu entry
#This (or something like it) should be in your configuration
root   (hd0,2)
initrd /initrd.img-2.6.10-5-386
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda4

title  Ubuntu, 2.6.10 #Another 32-bit Ubuntu entry
#This is an example of an Ubuntu entry which does not have a separate /boot/ partition
#(it is provided only as an alternate to the example above -- do not use them together)
root   (hd0,2)
initrd /boot/initrd.img-2.6.10-5-386
kernel /boot/vmlinuz-2.6.10-5-386

title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1

Now this one doesn't have Fedora on it, but what you are going to have to figure out is what the root (hd0,#) is for both situations and then add new lines into the grub file (they will be duplicates but with different root  (hd0,#) for them. You can even customize the description line so you can differentiate between with external or without.
 Here's what you need to do.
When first booting hit SHIFT to enter the grb menu, then hit E to edit the grub menu. This is only a TEMPORARY edit, so keep notes on what you do. Go to the line for Ubuntu (without the external drive plugged in) and edit the root  (hd0 ,1) line and plug in a different number, say 0 or 2. Now test it by telling grub to boot to it. If it boots correctly to Ubuntu you know thats the new number you'll change it to. If not reboot and try a different one until you get the one you want. 
 before you go any farther make a backup of your grub file, just in case you want to go back sudo cp /etc/defaults/grub  /etc/defaults/grub.orig
  Once you have them figured out you can edit the to /etc/defaults/grub file to put in the correct numbers and add any lines for when the external drive IS plugged in if needed.
Once your done editing save it and type update-grub and it will save it to the system.
It's going to be a pain in the butt, but it should work. NOTE - This is what I had to do for Grub 1.5, but I am pretty sure I told you the proper way to update grub 2.0. I'd take a few minutes to read [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   so you get a good understanding of the new grub process

---

