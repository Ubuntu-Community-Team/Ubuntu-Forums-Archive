---
title: "Partition difficulties"
date: 2011-11-07
forum: General Help
---

### Post by Roter1337 on 2011-11-07
Hello, I used to be a fervent user of microsoft windows 7, but since natty I formatted my drive, and did a full ubuntu install. I really love ubuntu, but there are some applications that just can't run through wine no matter how many workarounds you use. I want to reinstall windows 7 as a seperate partition, I used gparted and created a 400 gig ntfs partition, but now Im trying to install windows 7 to it, but I get the error that the disk is part of The GPT partition style. I love oneric, and use it for everything, but I just need this partition to run battlefield 3 and other games, I really would not like to erase the 600 gigs of data I have accumulated on my ubuntu side, please help.


----
Roter1337

---

### Post by Roter1337 on 2011-11-07
Im not sure what to do at this point.

---

### Post by b0b138 on 2011-11-07
In gparted, click view-->device information.  What is the partition table type?

---

### Post by bluexrider on 2011-11-07
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=windows+7&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=windows+7&sa=Search)

---

### Post by Roter1337 on 2011-11-07
b0b138, its gpt
bluexrider That was not very helpful to my problem

---

### Post by b0b138 on 2011-11-07
:(  You're pretty much stuck. You would need to backup all you data so the drive can be completely redone using ms-dos/mbr partition table instead of gpt.

Here's a site with something about converting, but it doesn't seem to be guarantied  [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by Roter1337 on 2011-11-07
Thanks for the help

---

### Post by Mark Phelps on 2011-11-08
Haven't tried this, but according the text in the link, if you change the NTFS partition type using fdisk, you can then install Windows:

[http://blog.elsdoerfer.name/2010/05/21/booting-ubuntu-karmic-and-windows-7-from-a-gpt-partition-using-bios/]("http://blog.elsdoerfer.name/2010/05/21/booting-ubuntu-karmic-and-windows-7-from-a-gpt-partition-using-bios/")

---

