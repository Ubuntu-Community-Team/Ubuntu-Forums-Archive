---
title: "HD 640GB but free space is 540 just after a format !?"
date: 2010-10-05
forum: General Help
---

### Post by awd01 on 2010-10-05
[SIZE=6]**[COLOR=DarkOrange]Hello[/COLOR]**[/SIZE] guys, i am new to your site and also new in linux!

I use[COLOR=DarkOrange] Ubuntu 10.04[/COLOR] and i have a HD 640GB.
The story is like this. I run ubuntu with a usb I install them and when it asked me if I want to install ubuntu aside with windows I selected no. So I selected the option that you erase all your data and you put just the ubuntu. When my computer was running normaly I saw the properties of my hard drive and i saw that my free space is 544.5 GB !  What exists in 100gb??? I there any chance that windows didnt erased completely? I say that because my free space in windows was around 540 GB. Should I format again?

---

### Post by ezsit on 2010-10-05
> I saw the properties of my hard drive and i saw that my free space is 544.5 GB ! What exists in 100gb??? I there any chance that windows didnt erased completely? I say that because my free space in windows was around 540 GB. Should I format again?

If you only had 540GB free space in Windows and you now have 544GB free space in Ubuntu, doesn't this mean that the Windows and Ubuntu installation took the approximately the same amount of space?

Also, check the partition layout. Ubuntu will create a swap partition that could be the size of your RAM or bigger. Also, the manufacturer may have a restore partition somewhere on the drive that did not get erased. Just some thoughts. And, Linux disk formatting will use a bit more space than NTFS formatting and Linux also reserves 5% of the hard drive for root use only.

---

### Post by XeonBloomfield on 2010-10-05
It seems to me that you have installed the systems side by side.

Check in Disk Manager partition layout looks like.

---

### Post by neoragexxx on 2010-10-05
Hi, even if you selected not to install with windows side by side , did you by any chance have another partition before installing ubuntu ? For example

partition for windows
partition for media, other files etc.

If this is the case then you just found where your missing GB are, if not maybe someone else can help you

---

### Post by matt_symes on 2010-10-05
Hi,
 
There can be a number of reasons for this. When you installed ubuntu it is lihtly to have installed a swap partition for you. This allows you to emulate more physical memory than you actually have (Generally a good thing). The file system itself also uses hard disk space. It needs to store structures on the drive that allow it to identify programs and where they are. All file systems do this including mac and windows.
 
It you want to view your partitions, go to system->administration->gparted. This will should you what partitions you have on your drive and you can see what size they are.
 
If you want to view disk usage, open a command prompt and type df -h.
 
Kind regards and welcome

---

### Post by awd01 on 2010-10-05
Guys i want to thank you all for your instant reply!!!!!

OK. Here are my results-answers.

1. I run GParted  my results are:     model ATA WDC WD6400AAKS-6 , size 596.17 GiB
  4 partitions:                                                    
-   unllocated  unllocated  size 1MB
-   /dev/sda1  ext4  587.52GB
-   /dev/sda2  extended  8.65GB
-       /dev/sda5  linux-swap 8.65GB 

 2. after the command df -h
  
  awd01@awd01-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             579G  4.5G  545G   1% /
none                  1.5G  316K  1.5G   1% /dev
none                  1.5G  736K  1.5G   1% /dev/shm
none                  1.5G  192K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

if we add all the partitions the result is way smaller than the 640GB... i dont get it

---

### Post by dabl on 2010-10-05
Boot a Live CD and start GParted.  Use that to look at the hard drive.  It should be obvious how many partitions there are, and how full each one is.

---

### Post by awd01 on 2010-10-05
> **dabl said:**
> Boot a Live CD and start GParted.  Use that to look at the hard drive.  It should be obvious how many partitions there are, and how full each one is.

its different than using the application from the System> Administration > GParted ?

---

### Post by coffeecat on 2010-10-05
> **awd01 said:**
> 1. I run GParted  my results are:     model ATA WDC WD6400AAKS-6 , size 596.17 GiB
  4 partitions:                                                    
-   unllocated  unllocated  size 1MB
-   /dev/sda1  ext4  587.52GB
-   /dev/sda2  extended  8.65GB
-       /dev/sda5  linux-swap 8.65GB 

....

if we add all the partitions the result is way smaller than the 640GB... i dont get it

In fact they add up very well, but you've misread and misquoted the Gparted sizes. Gparted reports in [gibibytes]("http://en.wikipedia.org/wiki/Gibibytes") GiB, whereas the 640GB of your hard drive is in [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte") GB.

640GB (gigabytes) is approximately equal to 596 GiB (gibibytes).

**Edit:** actually, the three sizes you've given add up to 596.17 because sda5 is inside sda2, and you've given the  596.17GiB on the top line.

---

### Post by awd01 on 2010-10-05
> **coffeecat said:**
> In fact they add up very well, but you've misread and misquoted the Gparted sizes. Gparted reports in [gibibytes]("http://en.wikipedia.org/wiki/Gibibytes") GiB, whereas the 640GB of your hard drive is in [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte") GB.

640GB (gigabytes) is approximately equal to 596 GiB (gibibytes).

**Edit:** actually, the three sizes you've given add up to 596.17 because sda5 is inside sda2, and you've given the  596.17GiB on the top line.


ooh yes... i see!!! I thought that GiB is GB ... i havent hear before for gibibytes...
nice!!! Thank you very much!!!

---

### Post by coffeecat on 2010-10-05
> **awd01 said:**
> ooh yes... i see!!! I thought that GiB is GB ... i havent hear before for gibibytes...

It is confusing. The Wikipedia articles I linked tell the full story, but for simplicity:

1 Gigabyte (GB) = 1000x1000x1000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 bytes.

The problem is that many people say gigabyte when they should say gibibyte. It's something of a tradition in the computer world, but strictly wrong because the prefixes giga-, mega- and kilo- are from the International System of Units and are all multiples of 1000. With multiples of 1024, we should be saying kibi-, mibi- and gibi-bytes.

Hard drive manufacturers use gigabytes because it makes their drives look larger and RAM module "gigabytes" are really gibibytes because they are multiples of 1024. But you don't hear many people referring to a 2 gibibyte memory module.

Did I say confusing? :)

---

### Post by tedygram311 on 2010-10-05
> **awd01 said:**
> its different than using the application from the System> Administration > GParted ?

Not really but when you boot from the CD you aren't using any partition and you are able to edit all partitions... can't edit a partition that you are using currently.  I am about 100% positive that this is correct  but if someone would like to correct me I would appreciate it so that I don't look like a complete fool =)

---

