---
title: "Creating Partitions?"
date: 2006-02-28
forum: General Help
---

### Post by christopher.pascual on 2006-02-28
I was wondering if anyone could lend any insight as to why I am not able to create a new partition through Gparted. 


The current paritions on my HD appear, but the options to create or resize are greyed out.

Any ideas?

Thanks

---

### Post by Jimmey on 2006-02-28
For you to be able to make a new partition, there needs to be empty space for that partition to occupy. If there is, select the empty space, and click new. If not, you need to re-size another partition:

You cannot re-size an active partition. If you're using Ubuntu, and want to re-size Ubuntu's partition, I'd suggest booting into the liveCD to do it.

Hope I've shed some light.

---

### Post by christopher.pascual on 2006-02-28
right, the thing im not understanding is why it is not letting me resize my ubuntu partition. 

I will try the livecd method.

---

### Post by Ramses de Norre on 2006-02-28
You cannot make changes to a mounted partition, so unmount the partitions.
In case it's your root partition you will indeed need to use a live cd.

---

### Post by christopher.pascual on 2006-02-28
ok i tried the livecd method, but the problem is that the ubuntu livecd won't recognize my video card so X won't start

i have one of those linux system rescue cds that has qtparted on it, but when i try to get it to run, it says that it can't find any drives because i am not the root user.... 

it is a sata drive if that makes any difference

---

### Post by aysiu on 2006-02-28
[QUOTE=christopher.pascual]
i have one of those linux system rescue cds that has qtparted on it, but when i try to get it to run, it says that it can't find any drives because i am not the root user.... [/QUOTE] Is it Knoppix, by chance?

P.S. I've never had any problems [using DiskDrake to partition](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by Ramses de Norre on 2006-02-28
Does X work when you use vesa as driver?
And shouldn't give a rescue disc you the option to log in as root? You can hardly save anything when you're not..

---

