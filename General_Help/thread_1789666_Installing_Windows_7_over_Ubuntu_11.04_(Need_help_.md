---
title: "Installing Windows 7 over Ubuntu 11.04 (Need help as soon as possible!)"
date: 2011-06-24
forum: General Help
---

### Post by TheMidnightWings on 2011-06-24
I know this seems odd, but here, I am getting this error when I launch the exe. I don't know what to do! 
Please, need help A.S.A.P if necessary :/

---

### Post by ajgreeny on 2011-06-24
Windows can not read or use any of the linux file systems, eg ext4, so does not think there is a hard disk to install to.

If you want to get rid of ubuntu entirely you can run the live CD of ubuntu and use gparted to delete all or some of your ubuntu partitions, thus making unallocated space, which the windows installer wil now see.

You could also just reduce your ubuntu partition size and then install windows in the free space  Grub would then need to be restored to get a dual boot, but that is the work of about 60 seconds only, so not to be thought of as a great problem.

---

### Post by Joris Donders on 2011-06-24
Well, ....... ok let's rock ! 

First you've got to use a LiveCD from Ubuntu (any version from 10.04 on will do)

So insert the CD and let the computer reboot with the CD in it. (I hope that you know that you've got to set the BIOS-bootorder straight; first the DVD-player than HD and so on) 

Let the CD do it's thing and select "Try Ubuntu"; let it do what it does. And if all went well you come into a Gnome panel with all Menu's and stuff. 

Don't panic ! Go to System/ Control/ GParted and run the program. 
Format your entire disc to NTFS (you can select that) So, completely wipe it and format it as said. This can take a little time, depending on the size of your harddrive. 

When it's done, take out the disc and insert now your Windows 7 DVD. 

Same again, reboot (with the disc in it) and let the Windows installer do it's thing (this takes a HUGHE time ! It takes for a complete installation for about 3 to 4 hours; so get a thermos coffee !)

And your done ! 

May I ask why you switched to Windows 7 ? Did you encouter problems with Ubuntu or is it just for fun-purposes ?

OOPS ; this topic was already answered .... sorry I think I was sleeping  lol

---

