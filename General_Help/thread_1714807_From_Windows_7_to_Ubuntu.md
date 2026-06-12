---
title: "From Windows 7 to Ubuntu"
date: 2011-03-25
forum: General Help
---

### Post by merfm on 2011-03-25
Hi everybody,

This is my very first post here. I just decided to quit Windows and install Ubuntu at my laptop, but I would like to be able to keep my Windows (and MS Office) for a while, as I have some compatibility problems when opening my old MS Office documents with Open Office.

I considered installing Wuvi, but Windows 7 is not in the list of Operating Sistems supported. Can anyone give me a clue?

Thanks in advance!!!! :)

---

### Post by garvinrick4 on 2011-03-25
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
#defrag Windows 7 a couple of times to start with.
#Download .iso file of ubuntu as instructed above: Good instructions for installation above link.
#After burn your CD boot off of it and choose install along side other O.S. and will give
  aprox. half of your drive to Windows and half to Ubuntu.

---

### Post by merfm on 2011-03-26
Thnks for the reply, garvinrick4.

I still have one doubt: will this method create a partition in my hard drive? I would prefer not so, this is why I was intending to install Ubuntu via Wuvi.

---

### Post by Hedgehog1 on 2011-03-26
> **merfm said:**
> This is my very first post here. I just decided to quit Windows and install Ubuntu at my laptop, but I would like to be able to keep my Windows (and MS Office) for a while, as I have some compatibility problems when opening my old MS Office documents with Open Office.

You will need to do some partitioning to operate two Operating Systems in a dual boot situation.  However, the process is reversible if you later decide that Ubuntu is not for you.

Here is a picture of a disk drive with 3 NTFS/Windows partitions, and one extended partition with 3 Linux/Ubuntu partitions in the extended partition.

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]

***The Hedge***

:KS

---

### Post by The Cog on 2011-03-26
> **merfm said:**
> TI still have one doubt: will this method create a partition in my hard drive? I would prefer not so, this is why I was intending to install Ubuntu via Wuvi.
Yes it will. It also installs a custom bootloader (GRUB) that offers you the choice of Ubuntu or Windows when you power on.

Wubi on the other hand, will create a large file on your Windows partition to use as a virtual disk. Performance shouldn't be much worse than using proper partitions. 

If you want to change later and extract the wubi setup to a separate partition, I think I saw that it's possible but I don't know how hard it is.

---

### Post by garvinrick4 on 2011-03-26
Look up tutorials by rubi1200 he is very adept at Wubi installs.
EDIT: Here is a good link: incase of any mishaps: Nice to bookmark:
I have install of WUBI 9.10 that I have had since 9.04 and has been
very stable for a couple of years now, very stable.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by ARMNHIE on 2011-03-26
You could always install Wine. Applications > Ubuntu Software Center; search for Wine; I recommend the 1.2 Gecko version. Installing wine will let you install Microsoft Office and run it smoothly. You can visit [http://www.mybuntu1.com](http://www.mybuntu1.com) and search for Wine. There's some more in depth installation help there.

---

### Post by garvinrick4 on 2011-03-26
I myself prefer the partition install. If you choose to remove Ubuntu you can do it in one 
partitioning program in a few minutes and give the ubuntu partition back to Windows very
simply. Do what you feel comfortable with but do not fear partitioning the software does it
all. If you choose Wubi ask rubi1200 which is the best version of Ubuntu to use.

---

### Post by garvinrick4 on 2011-03-26
You have a nice machine I hope you made your 3 Windows 7 disks and the recovery disk
when you first got machine or received your disks with machine.
*always keep your Windows disks and your ubuntu disks with your laptop. You can do 
anything as long as you have disks, anything. You can rest your mind at all times if you 
have your personals backed up and your disks. Enjoy your Ubuntu it is a kick.

---

