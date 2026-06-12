---
title: "Satan is corrupting my hard drive!"
date: 2010-08-27
forum: General Help
---

### Post by minigilani on 2010-08-27
Ok, my logical drive was accidently deleted, and along with it, it took a (almost) 130 GB NTFS partition, my Backtrack 4.0 partitions, and my Kubuntu 10.04 partitions - the former containing GRUB Stage 2, i believe.. i could afford to lose the OS partitions, but not the NTFS partition, so i fired up testdisk to restore my partitions, and i expected it to work flawlessly, seeing that i hadn't messed up any data on that bit of the drive.. it showed me the partitions exactly how they used to be, so i decided to write them back.. now i have a problem..
whenever i boot up in Ubuntu or Backtrack, i can see the partitions mounted! I can view pictures, and stuff.. but whenever i run GParted to install Ubuntu back (i still can't boot with GRUB, error 22) i see the whole hard disk as unallocated space.. i am completely scared outta my wits..
.
To top all this, i'm a noob!! Only been using the GUI for about a year (Gnome, just switched to KDE), lately been reading up and trying to learn the CLI, and we all know how scared noobs get, when faced with such problems..
.
I have to boot off of live cds to get online!!

edit: btw, i have WinXP on the first partition.

---

### Post by Rubi1200 on 2010-08-28
First and foremost, you should be concerned with trying to save any data you can; reinstalling can come later if needs be.

Also, since you are using a LiveCD please post the results of the bootscript linked to at the bottom of my post so we can get a better overview your setup.

---

### Post by minigilani on 2010-09-10
Ok, i fixed it. I made a slight error when restoring my partitions through testdisk, my NTFS partition was a logical drive, i accidentally selected it as a primary partition during the restore process.. i believe Gparted is a bit finicky when it comes to reading hard disks. Anyways, i fixed it.
Thanks Rubi =D

---

### Post by Chronon on 2010-09-10
If you edit the topic title and mark it as solved this topic will stand a better chance of helping others later.  I'm glad your problem is solved.  :)

---

### Post by minigilani on 2010-09-17
Done, thanks Chrono.

---

### Post by Rubi1200 on 2010-09-17
You are more than welcome :)

---

