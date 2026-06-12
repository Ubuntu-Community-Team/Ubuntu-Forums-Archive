---
title: "install and boot on drive 2?"
date: 2010-08-14
forum: General Help
---

### Post by rchubcitywihwy1480 on 2010-08-14
i have 2 drives on a pc i am having updated, if i take all contents off the 160 drive, can i install ubuntu on it?  do i have to do anything else to the drive?  when i boot,  which keys or how do i then boot back and forth,?  vista home premium is on the  main drive.  a new mother board had to be installed, was an amd 64 x2 4600, not sure what changes were made
tks

---

### Post by Mark Phelps on 2010-08-14
Do the following:
1) disconnect the Vista drive
2) connect the other drive
3) boot from the Ubuntu CD
4) install Ubuntu and GRUB
5) reconnect the Vista drive, but continue to boot from the Ubuntu drive
6) boot into Ubuntu
7) open a terminal and enter "sudo update-grub".  This should regenerate the GRUB menu and add an entry for Vista
8) reboot.  Should now have a GRUB menu with an entry for Vista

---

### Post by rchubcitywihwy1480 on 2010-08-14
Guess i am doing something dangerous for me!  How do you disconnect the vista drive?

sorry
tks

---

### Post by ranch hand on 2010-08-14
I would check your bios.  There may be a way of just turning off one or the other drive.

It is hard to say as you give no details on your hardware.

If there is no such option you just need to open up the case and unplug the bugger, crud but effective.

All of this is assuming that you are using SATA drives.

---

### Post by rchubcitywihwy1480 on 2010-08-14
i won't know hardware till i get the system back, but those steps  don't sound to interesting, i thought there were some discussions here where you could do this simpler on 2 separate drives?

tks

---

### Post by worksofcraft on 2010-08-14
If you already have Vista installed you should not have to disconnect any drives because Ubuntu is very friendly to pre- existing operating systems.

Installation will tell you about them and in principle all you have to do is select "Install side by side". However as you want to keep them each on their own separate drive (an excellent idea IMO) you best manually choose the partition you want for Ubuntu.

---

### Post by oldfred on 2010-08-14
I am not as big of a fan of unplugging a drive as others are but you have to use the advance button on the last screen or grub will install its boot loader over the windows boot loader.

(lucid is similar)
Install karmic Screens shown with advanced button
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by ranch hand on 2010-08-14
> **oldfred said:**
> I am not as big of a fan of unplugging a drive as others are but you have to use the advance button on the last screen or grub will install its boot loader over the windows boot loader.

(lucid is similar)
Install karmic Screens shown with advanced button
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
That advanced button is the least you should do.  The installer for 10.04 has been known to eat the boot sector of MS installs.  I do not think that bug has been completely fixed.

Make REAL sure that it is being installed on drive MBRs only.

---

### Post by rchubcitywihwy1480 on 2010-08-14
After i get the system back, i'll check back.
tks

---

### Post by rchubcitywihwy1480 on 2010-08-16
If i transfer all my dta to a backup drive, what do i have to do to put it on the c drive with vista home premium?

It wa a amd athlon 64 x2 4600, with a 160 sata and a 160 backup, a new mb was put in so i am not sure what else has changed.  

I have the cd  i think it was 10.?

I think this might be the simplest?  Tuesday  i am getting it.

tks

---

### Post by ranch hand on 2010-08-16
If you are using the 160Gb drive I would make the partitions in advance using gparted on the Live DC.

I would make a 20 or 25 Gb ext4 partition, and a 75Gb ext4 partition at the start of the drive.  I would put a swap partition at the end of the drive.  Ubuntu recommend that swap be twice as big as you ram.

The rest of the drive I would format to what ever you need for your back up files.  Surely 50+GB would be enough.

When you install you want to know the names of the partitions so that you can use the "manual" option on the installer partitioner and tell it where to install.  You want to have the mount point for the 20-25GB partition as / which is the root partition and the 75Gb partition mount point as /home.  This gives you a more robust install than having it all on one partition.  You edit the partitions by simply right clicking on them in the installer partitioner and choosing the "change" option.

You must have 10.04 (10=year, .04=month of release).

---

