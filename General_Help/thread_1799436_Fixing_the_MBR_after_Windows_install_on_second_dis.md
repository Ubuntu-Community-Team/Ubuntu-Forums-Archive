---
title: "Fixing the MBR after Windows install on second disk"
date: 2011-07-07
forum: General Help
---

### Post by dhubbard on 2011-07-07
Does anyone know of an online tutorial for my issue below? I'm stumped and haven't been able to find anything.

I recently had to install Windows on my machine (long story), I installed it on separate drive from my Ubuntu install. So now when I boot my computer it goes into the Windows boot loader, rather than using GRUB2. I followed the directions at:

[https://help.ubuntu.com/community/Grub2#Copy](https://help.ubuntu.com/community/Grub2#Copy) LiveCD Files

but with no success (I'm guessing because Windows is on a different drive. I was also looking at:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

which does go into having Windows on a second drive, but nothing on using GRUB2.

---

### Post by seawolf167 on 2011-07-07
Just want to make sure - you followed the instructions under the section from [this page ]("https://help.ubuntu.com/community/Grub2#Methods%20of%20Reinstalling")and mounted and installed GRUB to the correct device?

Also, check in BIOS so that you have it set to boot off your drive containing your Ubuntu installation first (before attempting to boot off the separate Windows drive)

---

### Post by dhubbard on 2011-07-08
Ah, do I feel stupid. 
I changed the boot order of my drives (I would have thought sda would be first - but sdc was) and got into GRUB. I also had to follow the instructions again (for some reason my USB drive was listed as sdc.

---

### Post by 987a654 on 2011-07-08
I have somewhat similar setup, 
Got Ubuntu and Windows 7 on two HDDs, 
Correct me if I am wrong.
If I select Ubuntu HDD as primary boot device in the BIOS, it should automatically pick up Windows 7 from the second HDD?

Is there any manual editing like adding devicemap command?
From what I understand Windows does not like to be on a secondary drive. 

Yudi

---

### Post by seawolf167 on 2011-07-09
> **dhubbard said:**
> Ah, do I feel stupid. 
I changed the boot order of my drives (I would have thought sda would be first - but sdc was) and got into GRUB. I also had to follow the instructions again (for some reason my USB drive was listed as sdc.

Glad you got it working :)

---

### Post by seawolf167 on 2011-07-09
> **987a654 said:**
> I have somewhat similar setup, 
Got Ubuntu and Windows 7 on two HDDs, 
Correct me if I am wrong.
If I select Ubuntu HDD as primary boot device in the BIOS, it should automatically pick up Windows 7 from the second HDD?

Is there any manual editing like adding devicemap command?
From what I understand Windows does not like to be on a secondary drive. 

Yudi

Easiest way is to make the first boot device the hard drive with GRUB on it, then when GRUB loads, it will point to the partition boot record containing the Windows 7 loader. You can have it autocheck for other installed operating systems by running the following commands in a terminal

```
sudo apt-get install os-prober
sudo update-grub
```

---

### Post by MZ250Supa5 on 2011-07-09
I recently had a similar problem, and looked at the various instructions on the many forums and websites, and found it all either very confusing, or long-winded. This led me to thinking that surely there must be an easier and pain-free way of re-instigating GRUB2, and there is. It's called Rescatux, currently version 0.28, which as the name suggests is a rescue disc for not only Linux, but Winders as well.  Really brilliant, GRUB2 back up and running in 3 minutes with all the options including Windows, and that includes the live CD booting.  Completely pain free.  Maybe Rescatux isn't the solution to life, the universe and all things, but it does fix that annoying problem of losing the GRUB2 MBR when you've been so rash as to install Windows *after* Linux. 

Get Rescatux 0.28 here 

[http://www.supergrubdisk.org/category/download/rescatuxdownloads/](http://www.supergrubdisk.org/category/download/rescatuxdownloads/)

---

### Post by 987a654 on 2011-07-12
> **seawolf167 said:**
> Easiest way is to make the first boot device the hard drive with GRUB on it, then when GRUB loads, it will point to the partition boot record containing the Windows 7 loader. You can have it autocheck for other installed operating systems by running the following commands in a terminal

```
sudo apt-get install os-prober
sudo update-grub
```

Excellent, the Grub manual threw me off a bit, but thank you very much.

Second disk's MBR has win 7 boot manager, so dont have to worry about win 7 wiping grub form the first disk's MBR. 

Thanks once again.

---

### Post by seawolf167 on 2011-07-12
Not a problem - glad it worked

---

