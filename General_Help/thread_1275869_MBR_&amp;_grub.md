---
title: "MBR &amp; grub"
date: 2009-09-26
forum: General Help
---

### Post by texas.chef94 on 2009-09-26
Ubuntu was loading on this new HD mentioned as I was posting this and finished with an error 18. Please tell me there is a way to get out of this without having to reload windows. I guess XP is all this huge HD and this BIOS can stand

I am learning that all OS are not developed equally friendly, nor are forums.
This is not a rant merely an observation. I tried installing Mepis is absolutely horrible results as well as poor direction after the fact. Error 18 I am told has happened frequently which requires some menu.1st massage but no specifics. Another This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.
This may well be the problem but has to be a work around. Windows has no objection to the 160 GB HD.
Why am I here because I get results here and I am hoping someone has a clue.
Finally Mepis gives one the opportunity to load grub to root and I was curious as to what the access procedure was in such a configuration.
If I am out line posting this here add a comment, ignore or whatever. It was worth a shot

---

### Post by louieb on 2009-09-26
Still have your XP CD? Boot and select recovery mode. At the password prompt just leave it blank (unless you have set one in the past) then run 

```
fixmbr
```That should get it booting XP again. 

As for GRUB error 18 the traditional work around is to create a partition near the start of the disk, mount it as /boot and the installer will put your boot files in it.  Last I heard the limit was raised to 137GB on some machines.  Newer PCs have even a higher limit now. 



BTW: Windows can get an error too if its boot files are stored too far from the start of the disk. Its just luck or bad luck.

---

### Post by texas.chef94 on 2009-09-26
> **louieb said:**
> Still have your XP CD? Boot and select recovery mode. At the password prompt just leave it blank (unless you have set one in the past) then run 

```
fixmbr
```That should get it booting XP again. 

As for GRUB error 18 the traditional work around is to create a partition near the start of the disk, mount it as /boot and the installer will put your boot files in it.  Last I heard the limit was raised to 137GB on some machines.  Newer PCs have even a higher limit now. 



BTW: Windows can get an error too if its boot files are stored too far from the start of the disk. Its just luck or bad luck.

Thanks but I downloaded super grub what a neat tool. Let me ask you are you aware of how to partition to fool so to speak the BIOS into believing the HD is smaller. There is a way/ What is happening is the selected cylinder exceeds the maximum supported by the BIOS. So I create a linux partition, install ubuntu and get an error 18.
Now I have a BIOS upgrade to install, but one wrong move and the PC becomes a door stop.

---

### Post by louieb on 2009-09-26
It use to be that some hard drives had a capacity limiting jumper. It was used to fool BIOS into thinking the drive  is smaller that it actually is. Not really a good fix for you - but some of the older BIOS would refuse to boot if the hard drive inside was to big.

What I think I would do is get a 2nd drive, is your old one still good?  Its a lot safer for your data than trying to repartition to get around GRUB error 18. 

For a single drive you will need to get the  kernel stored close to the start of the drive. Maybe partition something like this 


[LIST=1]
[*]20GB for XP
[*]10GB - for Linux
[*]1GB - for Linux swap
[*]rest of drive - one big partition for your data.
[/LIST]
That would keep the kernel close enough to the start of the drive to prevent Grub error 18. And has the advantage of separating your data from the Operating Systems.   

Don't know how close to the start you need to be just guessing its either 33GB or 137GB depending on the age of your bios. 

> 
Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit _______________________________(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)
                                     

Btw that information came from [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")  it an information packed site almost overloaded, but for dual booting if you need to find something its probably there.

---

