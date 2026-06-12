---
title: "Disk failure or virus?"
date: 2010-08-30
forum: General Help
---

### Post by ked on 2010-08-30
Last night when I turned on my lap top (5 year old Acer TravelMate 4650), it was not able to boot up (10.04 LTS). No system files could be read and a lot of error messages was displayed. In fact, it has done a few checks for disk error lately during boot up, but no further warnings given.
I gave up recovering, and simply re-installed Ubntu 10.04.
I was wondering if this could be related to a virus attack?

Cheers,
Kare

---

### Post by akoskm on 2010-08-30
> **ked said:**
> Last night when I turned on my lap top (5 year old Acer TravelMate 4650), it was not able to boot up (10.04 LTS). No system files could be read and a lot of error messages was displayed. In fact, it has done a few checks for disk error lately during boot up, but no further warnings given.
I gave up recovering, and simply re-installed Ubntu 10.04.
I was wondering if this could be related to a virus attack?

Cheers,
Kare

I can hardly imagine a Linux virus attack on a personal laptop/pc.

---

### Post by WorMzy on 2010-08-30
Well, did you recently download any random shell scripts and run them with sudo?

---

### Post by ked on 2010-08-30
I've been using Linux for my computers since 1998, and never experienced this behaviour. I also noticed that occationally the laptop was incredibly slow when starting any application, like hanging for a couple of minutes, a sign of somthing heavy running in the background. Could not find any processes (running top) taking CPU power... hmmm, I wonder if the HD is struggeling... I'll find out after re-installing Ubuntu...

---

### Post by ked on 2010-08-30
In fact, I've been doing some installations with sudo, so it might very well be related to that. I'll try to be more careful hereafter... thanx!

---

### Post by 3rdalbum on 2010-08-30
5-year-old laptop? Your disk is possibly failing. Try going to System > Administration > Disk Utility and check the diagnostic results for your disk and see if the number of bad blocks has overtaken the number of spare blocks.

We don't get viruses here.

---

### Post by 3rdalbum on 2010-08-30
> **ked said:**
> In fact, I've been doing some installations with sudo, so it might very well be related to that. I'll try to be more careful hereafter... thanx!

It's still not likely to be this. Even trojans are almost unheard-of on Linux, and there are none at the moment that I'm aware of.

---

### Post by lucaasjohnson on 2010-08-30
Hi,
  May be there is virus attack on your system but it is also possible that there is problem in bootstrap loader. B'cos this type of problem occur due to error in files of bootstrap loader.

---

### Post by ked on 2010-08-30
> **3rdalbum said:**
> 5-year-old laptop? Your disk is possibly failing. Try going to System > Administration > Disk Utility and check the diagnostic results for your disk and see if the number of bad blocks has overtaken the number of spare blocks.

We don't get viruses here.

Does not look that bad (60 bad sectors on a 80 G disk). Got one warning saying "Current Pending sector count" with the value of 60. I guess it's referring the number of bad sectors. The disk holds a temperature of 50 deg C (122 F) Sounds a bit high to me... Self assessment and tests completed OK.

---

### Post by philinux on 2010-08-30
> **ked said:**
> Does not look that bad (60 bad sectors on a 80 G disk). Got one warning saying "Current Pending sector count" with the value of 60. I guess it's referring the number of bad sectors. The disk holds a temperature of 50 deg C (122 F) Sounds a bit high to me... Self assessment and tests completed OK.

Have a look through /var/log/messages and look for any disk read or write errors.

---

### Post by ked on 2010-08-30
> **philinux said:**
> Have a look through /var/log/messages and look for any disk read or write errors.

Not a single error message... Well everything reinstalled and seem to work fine now.

---

