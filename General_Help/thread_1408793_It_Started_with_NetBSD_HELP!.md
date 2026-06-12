---
title: "It Started with NetBSD HELP!"
date: 2010-02-16
forum: General Help
---

### Post by katiwhompas on 2010-02-16
My problems started when I thought it may be interesting to remake my LAMP into a Unix LAMP with NetBSD. Once I had done so I realized I did not have the time available to learn a new system that was much different then what I already know, so I went back to Ubuntu to get the server softyware... Below is some of the problems I have been dealing with. I now think it all is happening because I made the mistake of letting NetBSD update the bootcode in my master boot record to the "latest" version of the NetBSD BOOTCODE! what the hel, ummm heck do I do now to get my master boot record fixed?!?!
 
There is more... too much really it makes my spleen ache to consider these issues, but here goes.
I had Ubunto 9.04 on this box. I decided (after I had tried and got rid of NetBSD) I wanted to use it as a LAMP so got several downloads of 9.10 server from several systems and several providers. All had the same issue; the download of Make failed when I tried to install using the LAMP selection. I had been able to load the base system. Now I can not.
I tried to install the original Ubuntu 9.04 that I was using. it fails now. It freezes at the window that displays the desktop once in and running, but without any icons, buttons etc. Just the damn desktop picture.
When I try to install Ubuntu desktop 9.10 I get: (initramfs) stdin: i/o error
mount: mounting /dev/loop0 on //filesystem.squashfs failed: no such device
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
The odd part is I CAN install Windows XP Pro! Once it is in and running I try to install Ubuntu as a new system as I do NOT want to run inside windows, I get no reboot. If I ask for help with reboot it fails again there. I have swapped hard drives cd and dvd readers, video cards and I can see it was able to see and connect to my internet connection. This is a generic box with a older pentium 3 or 4. I have 2 gig of ram in it and all the drives have been 20 to 30 gigs each.
Any Ideas? I was at the server area as that was where I had started and was suggested I come here instead. I am not able to always write in here as I get a error from this site that says my message is too short and needs at least one character! So I have to copy this all from note pad in my main box in case I loose it all. I am using firefox in a win xp 64 pro generic box.
To make matters much worse I keep getting an error from this site that says my message needs to be at least one character long! then everything I wrote is gone. I can get in at times and not at others. I am beginning to think Ubuntu is not worth it, but I have put this in other machines for friends and clients with no problems. 
I am way behind in what I need to do, any help is very apreciated. 
There is one possible starting point for these problems... It all started when I tried NETBSD from the Berkeley collection. 
 
I am now trying to get this into the Ubuntu site with IE of all things! What is the free world comming to?!?!!
 
Thanks!

---

### Post by 199DMF on 2010-02-16
im not even going to read all that but ill igve you a bump

---

### Post by katiwhompas on 2010-02-17
I have no idea what combo I used... but it has been resolved to loading 9.04. 
 
9.10 is too much trouble...
 see below
 
 
Unfortunately testing the CD in my main windows xp system ended in my graphics card or my monitor being trashed. I did not install just clicked on try without installing. The monitor, etc were fine, the CD seemed to work as the desktop for 9.10 came up. 
I shut down at that point and on restart My system was totaly whacked.

---

