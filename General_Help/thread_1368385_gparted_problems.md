---
title: "gparted problems"
date: 2009-12-30
forum: General Help
---

### Post by spiky001 on 2009-12-30
Hi i posted this yesterday
[http://ubuntuforums.org/showthread.php?t=1367404&highlight=gparted](http://ubuntuforums.org/showthread.php?t=1367404&highlight=gparted)


since then i have tried hard drive again still not finding so i put hd in as 2nd drive formatted drive with disk uttility 

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa177a177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccf06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1027     8249346    c  W95 FAT32 (LBA)
spiky@server:~$ 
this is from fdisk sb1 is the disk. but still gparted wont find it. Any ideas plz?

---

### Post by jamesisin on 2009-12-30
I have two ideas.

First, don't post duplicate threads for a problem.  Continue your original thread.

Second, provide more detailed explanations of the problem you are facing.  On the one hand it seems that you have a running 9.10 system (capable of running Disk Utility) and it also seems that you are attempting to do a fresh installation of Ubuntu (using gparted as a partitioning tool).

---

### Post by spiky001 on 2009-12-30
Sorry about duplicate thread, i had a hard drive failure so put in spare drive (as of old thread)  i got original drive to start ok but thought i would load 2nd drive just in case.Gparted could not find it but bios dose boot screen sees it not gparted tried 3 different disc ( they have all worked before) so i used disk uttlity to format it then put it as main drive to load OS still not found by gparted but as u can see fdisk is ok? fdisk was used when it was fitted as 2nd drive hope this makes sense would like to get to bottom of this

---

### Post by jamesisin on 2009-12-30
So you have a working 9.10 system on which you used Disk Utility to format this new drive to ext3?

---

### Post by spiky001 on 2009-12-30
ok i had a 40 gig drive so i tried an old window disk 8 gig gparted cant find if booted on it,s own window me comes up, mean time i managed to get 40 gig running, so then i procided to format 8 gig to use as spare drive incase 40 gig died again my so formatted 8 gig but cant install anything on it sdb1 is the 8 gig hope this is clearer

---

### Post by Leppie on 2009-12-30
so you have karmic installed on the 40gig drive and now you would like to format the 8gig drive?
maybe a silly question, but are you using sudo to run gparted?
```
$sudo gparted
```

also, if you are trying to install things on the 8gig drive, did you mount it?

---

### Post by spiky001 on 2009-12-30
no i took the 40 gig back out put 8 gig in it,s place then tried loading OS from cd on to it as main drive. I formated it when it was 2nd drive as it had fat16 just thought that was causing probs. Gparted was did,nt find through normal install

---

### Post by jamesisin on 2009-12-30
Leppie - Is that what he meant?  Ok.  Shouldn't he use gksudo gparted rather than sudo gparted?

---

### Post by spiky001 on 2009-12-30
ok we have got crossed issues here, i,m not gparting it from within ubuntu but using a fresh install to main drive which is 8 gig have removed 40 gig. I used disk uttility from within OS purly to check drive that will not boot (GET PAST GPARTED) the sdb1 was to show 8gig drive dose work

---

### Post by jamesisin on 2009-12-30
Ah, I see.  Partition the drive from your working system as ext3 (or ext4 if you prefer).  Then attempt to run your installation media.

---

### Post by louieb on 2009-12-30
Do you know how to switch drives in Gparted?
Drop down box in upper right corner or try to have Gparted display the 2nd drive on startup.
```
gksudo gparted /dev/sdb
```
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by spiky001 on 2009-12-30
no i want to load OS on it 8 gig, it is now the only drive in pc but wont get past gparted on install there is no other hd in pc

---

### Post by jamesisin on 2009-12-30
So you run the installation and when you get to the section about partitioning you see no drives?

Have you tried downloading gparted as a live CD to see if gparted itself is able to see this hard drive?

---

### Post by Leppie on 2009-12-30
> **jamesisin said:**
> Leppie - Is that what he meant?  Ok.  Shouldn't he use gksudo gparted rather than sudo gparted?

not sure what he meant...
i don't believe that using sudo or gksudo makes a lot of difference running from a livecd.

---

### Post by jamesisin on 2009-12-30
I may have been quite confused.

---

