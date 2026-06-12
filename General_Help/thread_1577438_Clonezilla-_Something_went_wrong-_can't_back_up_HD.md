---
title: "Clonezilla- Something went wrong- can't back up HDD"
date: 2010-09-18
forum: General Help
---

### Post by Vigh on 2010-09-18
Hi,
 recently just tried to back up my system using clonezilla, it reported an error which said simply- something went wrong, please view the logfile for details. Where do I find this logfile? Really want to make an image backup of the HDD. As my linux system is running near perfect now.

Thanks

Ant

---

### Post by TimEnid on 2010-09-18
i had this error my first time using it as well. you have to make sure you select the correct partition that you want to back up, and select the correct place where you want to save it. That was my error, which i figured out on my own. You have to read the notifications.

---

### Post by Vigh on 2010-09-20
Still not working, going to try to change the file system of the back up device.

---

### Post by Mark Phelps on 2010-09-20
One thing I noticed when I first started using Clonezilla, especially when using more than one physical drive, is the the partition IDs were different from that in Ubuntu.

For example, in Ubuntu, I might have /sda1  and /sdb3 (for source and target partitions), while in Clonezilla, they would be quite different.

Make sure you verify the correctness of both the source and destination partitions -- given that they might be different from what you're used to seeing.

---

### Post by Vigh on 2010-09-20
Yeah I'm selecting the right devices for backing up the main-drive. It comes back with a SYNTAX ERROR and says please view /var/partclone/log for more details.

---

### Post by Vigh on 2010-09-22
Any ideas? Or could someone suggest another free open-source ghost-imaging software package I could use to back up my system, besides clonezilla? My linux machine is running perfectly now and I want to have a ghost back-up just in case. Regards

Ant

---

### Post by CharlesA on 2010-09-22
Which version of clonezilla are you using?

Hit Ctrl + Alt + F2

cd /var/log/

They are all there. :)

---

### Post by Vigh on 2010-09-23
clonezilla-1.2.6-20-amd64, will check out the logfile, thanks

---

### Post by Ghost_Mazal on 2010-09-23
Have you tried the "Ubuntu based" 32bit clonezilla ? Try that if you haven't.
 
Can you also add if you use "expert" mode or not and if expert mode what settings you using.

---

### Post by Vigh on 2010-09-23
Nah just running in beginner mode. My operating system is AMD64 will clonezilla 32-bit still work??? I backed up a windows machine and it worked perfectly to a USB-flash drive. I am however trying to back up my own machine now and its to an external HDD and is obviously ubuntu 64-bit, running 10.10 maverick development version.

---

### Post by Ghost_Mazal on 2010-09-23
Yes 32 bit clonezilla will work. Your OS doesn't matter as Clonezilla is an OS on it's own that starts up. Give it a try if you can find a copy.

---

### Post by Vigh on 2010-09-23
Cheers, Will let you know how it goes.

---

### Post by Kenny King on 2012-11-14
Hi,

I just experienced the same problem. Clonezilla does have a 64 bit versioin. But I use i486 version on my 64 bit machine!

It was strange. I could not use Ghost to do my backup on the machine that I could not use clonezilla on. But Ghost gave me an message saying a linux partition or something like that didnot unmount correctly.

I went on booting the machine that has Ubuntu server 64 bit installed, and then shut it down.

After that, Clonezilla work all fine.

Hope that helps.

---

### Post by wildmanne39 on 2012-11-15
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

