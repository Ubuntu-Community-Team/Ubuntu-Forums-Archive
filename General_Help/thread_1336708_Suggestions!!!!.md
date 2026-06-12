---
title: "Suggestions!!!!"
date: 2009-11-24
forum: General Help
---

### Post by nishant.singh28 on 2009-11-24
I  have a 320 GB hdd on my notebook. Of that, I have 297 GB available. I want to keep 200 GB for all my Data. The remaining 97 GB is to be shared for Windows 7 Professional 64 bit and Karmic 64 bit. Karmic will be my primary OS with Windows 7 for some exclusively Windows work ( gaming, some other college work ). How should I make these partitions and what sizes ( Data is fixed, I am asking about the Karmic and 7). Also, what is the easiest method to go about with the partitions and installation considering that I want be starting off on a clean slate by cleaning out all of my partitions except the system partition done by Dell and deleting them. I want to know how to create the three partitions easily and in what order should I install the OS's. I have the DVD for 7 and the CD for Karmic. I want to keep Grub 2 as the Bootloader so should I install 7 first and then Karmic?

---

### Post by Wiebelhaus on 2009-11-24
Yes. Seven First then Karmic.

---

### Post by nishant.singh28 on 2009-11-24
> **Wiebelhaus said:**
> Yes. Seven First then Karmic.
And what about the partitioning. Do I simply delete all the partitions during 7 install and leave out enough space for Ubuntu? And what should be the sizes such that Karmic + 7 = 97 GB

---

### Post by Wiebelhaus on 2009-11-24
> **nishant.singh28 said:**
> And what about the partitioning. Do I simply delete all the partitions during 7 install and leave out enough space for Ubuntu? And what should be the sizes such that Karmic + 7 = 97 GB

You can pretty much do it anyway you want or let Karmic do it for you. 7 Requires at the very least 15 gigs and Ubuntu 5-7gigs. If your not comfortable partitioning it yourself , then let the Karmic partitioner do it for you automatically during the install.

---

### Post by nishant.singh28 on 2009-11-24
Thanks. Well I am comfortable with the partitioning so I'll do it as I said. Also, thanks for your quick replies. The only thing I wanted to confirm was the order. Once that was done, rest is fine. You see, I'm not a super noob :D. I am pretty much seasoned with reinstalling 1 os on a comp but doing 2 os's is a first for me.

---

### Post by Wiebelhaus on 2009-11-24
> **nishant.singh28 said:**
> Thanks. Well I am comfortable with the partitioning so I'll do it as I said. Also, thanks for your quick replies. The only thing I wanted to confirm was the order. Once that was done, rest is fine. You see, I'm not a super noob :D. I am pretty much seasoned with reinstalling 1 os on a comp but doing 2 os's is a first for me.

Cool and Welcome!

---

### Post by Hypnoz on 2009-12-10
I did this same thing, and there are a few things you have to remember.

- You can only have 4 "primary" partitions. So make sure you make the 4th into an "extended" partition, then you can fill that up with many more.
- You can create a parition that is shared between windows and linux, but let windows format it as NTFS, it just lets windows read it easier.
- Consider leaving 20gb or so at the very end, to give yourself a chance to try out a new OS without wiping out your current ones.
 
Here is what my current dual boot partition scheme looks like
(Primary) DellUtility  150mb
(Primary) Dell RECOVERY  2gb
(Primary) Windows  80gb
(Extended) Rest of drive
     - /Boot 100mb
     - Linux 40gb
     - Swap 2gb
     - Empty 95gb  (let windows make this as ntfs, and any OS can read/write it)
     - Empty 20gb  Reserved for a new OS I might want to try

It doesn't matter which order really, but if you do windows second, you will need to boot with a Live CD to fix the grub boot loader. So probably doing Windows then Ubuntu. 

In /boot/grub/menu.lst make sure you have a stanza like this at the top of the OS choose list

title           Windows Vista sp1
root            (hd0,2)
makeactive
chainloader     +1

then set "default 1" at the top to make it choose Ubuntu as the default boot. Or, put the windows option at the bottom of the list and set "default 0".

Lastly, don't get attached to your setup at first. Make all your partitions, install your OS's, format the shared drive, and make sure everything works. Make sure you're happy with the partiton sizes, and THEN start moving your data on and installing apps. The first time I set up multiple partitions and dual-boot, I think I re-did it like 3 times before I got a setup that I liked.

---

