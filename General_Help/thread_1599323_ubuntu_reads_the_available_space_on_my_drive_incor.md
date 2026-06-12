---
title: "ubuntu reads the available space on my drive incorrectly"
date: 2010-10-17
forum: General Help
---

### Post by BcRich on 2010-10-17
hi 
I'm using Ubuntu 10.04 and it seems that the free space available on my hard drive is not being read correctly. My drive is a 500GB SATA drive which Ubuntu declares that I have a total of 493.9GB available for usage. This is correct, as I understand that when using ext 3 or 4 file systems some of the drive space (approximately 10% according to some posts that i've read) is reserved for system usage. This is not the problem. 
The problem lies in what nautilus is indicating as "free space" on the drive. For example when I check in Disk Utility what the size the drive is it confirms that it is indeed a 500GB drive with 493.9GB available for usage after it has been partitioned, with the extra partition that Ubuntu creates when it is installed reserved for system usage. This is to be expected.  
So currently I have a 493.9GB drive that has an operating system on it ie Ubuntu and no other OS. plus about 30GB of my media on the drive. when I check in Nautilus how much of my drive is being used it informs me that 36.8GB is being used.
so therefore I should have 493.9GB - 36.8GB available on my drive. This means I should have 457.1GB of available space on my drive. 
However Nautilus tells me I have 361.5GB available on my drive. So where are the other 95.6GB? If this number was just a couple of Gigs missing I would not be too concerned, but i'm missing almost 100GB! that seems a bit strange to me.
does anyone ave any suggestions as to what is happening here?
I'd be really grateful to hear from someone that can shed some light on this issue :)
many thanks

---

### Post by Vaphell on 2010-10-17
nautilus and other tools lie :)

1. there are 2 different but similar units to describe the amount of data or space and that leads to confusion
GiB (gibigyte, commonly called gigabyte) - legacy one, counted in powers of 2, 1GiB = 1024^3
GB (gigabyte) - proper one, 1GB = 10^9 (Giga is SI prefix for 10^9)

they are similar in value, but not the same - there is approx 7% difference (1GiB = 1.07GB)
this is the greatest problem, because of the decades of improper use of SI prefixes in the computer world there is a huge mess and you never know if GB means GB or GiB in a given context

2. by default system reserves 5% of space for root usage, with huge partitions 5% it's quite a lot of gigabytes :) you can change the percentage, even set it to 0 to reclaim all reserved space (not recommended especially on system partition)
in system monitor free space = available + root

3. filesystems have some overhead so they use few gigs for its own stuff

check if the numbers add up more or less, accounting for the things i wrote. You have 7% of GB/GiB confusion and 5% for root which is at least 12% and then there is a filesystem overhead.

---

### Post by matt_symes on 2010-10-17
Hi,

Application->Accessories->Disk usage analyser will give you a graphical view of you disk usage.

Also from the command line.

[http://www.howtogeek.com/howto/ubuntu/check-your-disk-usage-on-ubuntu-from-the-command-line/](http://www.howtogeek.com/howto/ubuntu/check-your-disk-usage-on-ubuntu-from-the-command-line/)

Also du and df from the command line

Kind regards

---

### Post by efflandt on 2010-10-17
Not sure what to make of Nautilus 2.32.0 (in 10.10).  It says Contents: 223,176 items totaling 128 TB (some contents unreadable) and Free Space: 42.8 GB (on a 50 GB USB partition).  I do have a 1 TB internal drive, but nothing on that is mounted.

df makes more sense:
**df -h**
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf1              50G  4.7G   43G  10% /
none                  3.9G  316K  3.9G   1% /dev
none                  3.9G  328K  3.9G   1% /dev/shm
none                  3.9G  136K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock
```

---

### Post by BcRich on 2010-10-19
hi matt-symes
thanks for the suggestion
running ```
sudo du -s -m
``` in a terminal returns ```
69738    .
``` I had to use sudo or it would not count my system files.
disk utility indicates that my drive is 493GB which is correct, but i have not been able to ind a way of getting disk utility to indicate how much space is being used of that total size.
thanks again for the help all :)

---

