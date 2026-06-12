---
title: "I would like to set up my hard drive to run both Ubuntu and Windows 7..."
date: 2009-07-21
forum: General Help
---

### Post by brizzenden on 2009-07-21
But I am still pretty new to linux and I am not sure how to partition the drive or whatever needs to be done to allocate space for both on my drive.

---

### Post by masux594 on 2009-07-21
I use [this guide]("http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/") to create the partitions of ubuntu.. In the same hdd of vista .. with win7 is the same thing..

Sysc, A

---

### Post by brizzenden on 2009-07-21
I am sorry I should have specified.  I don't have another OS running on my laptop right now other than ubuntu.  I tried to install Windows 7 RC the other day, but there was some major problem with the install so after messing up my partition I had to install Ubuntu (which was the only OS that would install at the time).

I just downloaded GParted, which I assume is what I will need to use to attain my goal here, but I am not sure what needs to be done with it.  I watched a video that showed that I had to use the "format to" option, but for some reason when I right click my drive, like the person did in the video, that option was gray.

Basically I tried to Boot and Nuke my hardrive and start from scratch, but it says there is some problem with my disk and that it is usually due to a disk with bad sectors.

Since Nuking it didn't work I tried to partition the drives in another way but it just f***ed my drive up by splitting it into two parts that were unnalocated and did nothing.  Essentially I needlessly deleted everything off of my laptop.  I re-installed Ubuntu like 5 minutes ago and here I am.  I have like 3 apps installed on here and I am further back than I was when I tried to take matters into my own hands.

---

### Post by masux594 on 2009-07-21
Maybe i don't understand..So, now u have a [non wanted] triple boot?

Sysc, A

---

### Post by brizzenden on 2009-07-21
> **masux594 said:**
> Maybe i don't understand..So, now u have a [non wanted] triple boot?

Sysc, A

I messed it up, so that my drive was broken into two partitions (or what I assume a partition is, I am only 80% sure what a partition really is) both unallocated.  Ubuntu seemed to be working in this state, so I figured I would try to install windows 7.  When I went to the custom install screen that prompted me to pick a partition there were two partitions.  So I selected the one that I THOUGHT I set up for Windows 7.  It gave me an error message (I can't remember what it said).  After this I went back to try something else and Ubuntu was messed up.

So I reinstalled it and the only option was to use the whole drive for Ubuntu.  The above posted guide showed the option to manually type in how much space is devoted to Ubuntu. That requires another OS to be installed on the computer already. So I can not go by that guide.  

So right now I am running ubuntu as the only OS, and it is currently using the whole drive.

---

### Post by merlinus on 2009-07-21
This should work with 7:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by bodhi.zazen on 2009-07-21
You can partition your hard drive with gparted, it is included on the Ubuntu live CD.

Put Windows on Primary partitions, as much space as you wish.

Ubuntu needs two partitions / (root) and /swap (well strictly speaking /swap is not necessary).

I would put the ubuntu partitions on logical partitions in an extended partition.

I would also make a shared /data partition, ntfs, to share data across OS.

---

### Post by brizzenden on 2009-07-22
> **merlinus said:**
> This should work with 7:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
Thanks, this guide actually worked.  I didn't need to use command prompt to partition the second drive during install though.  Guess 7 does that on it's own.

---

