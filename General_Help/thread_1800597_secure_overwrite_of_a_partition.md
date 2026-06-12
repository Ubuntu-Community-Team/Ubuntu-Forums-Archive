---
title: "secure overwrite of a partition?"
date: 2011-07-09
forum: General Help
---

### Post by javajames97 on 2011-07-09
THE STORY (can be ignored): i have a duel boot of windows and ubuntu, but recently i got a virus, but this things is leach like in appearance. I tried reinstalling windows, then reformatting the drive and reinstalling windows but i still have this same virus??? This is dead creepy for me because windows cant read any of the other partitions, which are all formatted for linux, in formats which windows does not have the capability to read. So i dont understand how this could have happened. There are many things that i am still to try -- including completely overwriting the MBR with a GRUB in case the virus somehow resides in there?? But i have decided to give up on windows from now, because, despite all the actions i have taken, it has failed me repeatedly. But having had these viruses 3 times, i have noticed something, the first time i had a virus was my fault, because i left my computer insecure. After i formatted my HDD following that virus, i noticed i had 10gb of space robbed from me, disk utility believed i had a 160gb drive, but Gparted and everything else told me that i only had 149.7gb of space??? now after this virus - which logically couldn't have happened without someone directly attempting to tunnel my computer as i had so much extra security - i lost 6gb of space from my HDD?? Sounds odd?

THE QUERY: So i want to know if (from ubuntu) it is possible to do a secure format (similar to with a mac - were it completely overwrites everything, instead of just deleting the links) although, possibly i am not going back to windows, ever.

---

### Post by coffeecat on 2011-07-09
> **javajames97 said:**
> After i formatted my HDD following that virus, i noticed i had 10gb of space robbed from me, disk utility believed i had a 160gb drive, but Gparted and everything else told me that i only had 149.7gb of space???

That's not a virus. That's a simple misunderstanding of the difference between gigabytes (GB - base 10) and gibibytes (GiB - base 2). 160GB is approximately 149GiB. Have a close look: Disk Utility reports the total size in GB as do manufacturers; Gparted reports in GiB.

1 GB = 1000 x 1000 x 1000 bytes
1 GiB = 1024 x 1024 x 1024 bytes.

---

### Post by javajames97 on 2011-07-09
also, i updated grub, but grub detected something on sda1 (the windows partition) despite the fact i formatted it, i copied that so i have the file backed up, should i delete this record from the devices list - or would  loose my HDD for that

how can i stop grub from picking it up so that i can automatically boot to ubuntu for the time being

---

### Post by javajames97 on 2011-07-09
> **coffeecat said:**
> That's not a virus. That's a simple misunderstanding of the difference between gigabytes (GB - base 10) and gibibytes (GiB - base 2). 160GB is approximately 149GiB. Have a close look: Disk Utility reports the total size in GB as do manufacturers; Gparted reports in GiB.

1 GB = 1000 x 1000 x 1000 bytes
1 GiB = 1024 x 1024 x 1024 bytes.

oh, right, stupid me

but it still says 6GB (not GiB) used on my old windows partition

and i definetely had a virus, which somehow came back 1 hour after rienstalling windows

---

### Post by coffeecat on 2011-07-09
It's theoretically possible you have a boot sector virus which could come back after re-installing Windows. The boot sector (including the embedding area) usually covers only the first 63 or 2048 sectors, so zeroing this out should deal with any boot sector viruses. But if you want to wipe the whole drive to be absolutely sure, you could use shred:

```
sudo shred -vzn 0 /dev/sdX
```

That gives you one pass of zeroes only, which should be enough. Substitute sda, sdb, or whatever for sdX. After doing this you will have no partition table, so you will need to re-create one using Gparted before creating your partitions. Be very careful to get sda/sdb/whatever right. I zeroed the partition table on my main drive with one careless slip of the typing finger once. Never again! :(

---

### Post by javajames97 on 2011-07-09
Thank you, that is very helpfull, i assume that the shred command (with that format) will overwrite everything, including the MBR?

thanks :(

---

### Post by westie457 on 2011-07-09
> and i definetely had a virus, which somehow came back 1 hour after rienstalling windows
Hi if you would still like to use Windows boot into Safe Mode with networking. Go to [http://www.superantispyware.com/](http://www.superantispyware.com/) and download and install the free version. Let it update and then do a full scan of your system. Go get a coffee or do something else to fill in the time while the scan completes. When finished delete everything reported (take no prisoners here). Then reboot as normal. All in order good. Still stuffed then go to [http://www.malwarebytes.org/products/malwarebytes_free](http://www.malwarebytes.org/products/malwarebytes_free) and download and install. _NOTE for this you need to load Windows as normal_ otherwise it will not install. Once installed update and do another full-scan. Coffee time again and delete everything reported. All in order now. Good. 

Still "borked" boot into a LiveCD and follow the advice here [http://ubuntuforums.org/showthread.php?t=395937](http://ubuntuforums.org/showthread.php?t=395937)

---

### Post by javajames97 on 2011-07-09
> **westie457 said:**
> Hi if you would still like to use Windows boot into Safe Mode with networking. Go to [http://www.superantispyware.com/](http://www.superantispyware.com/) and download and install the free version. Let it update and then do a full scan of your system. Go get a coffee or do something else to fill in the time while the scan completes. When finished delete everything reported (take no prisoners here). Then reboot as normal. All in order good. Still stuffed then go to [http://www.malwarebytes.org/products/malwarebytes_free](http://www.malwarebytes.org/products/malwarebytes_free) and download and install. _NOTE for this you need to load Windows as normal_ otherwise it will not install. Once installed update and do another full-scan. Coffee time again and delete everything reported. All in order now. Good. 

Still "borked" boot into a LiveCD and follow the advice here [http://ubuntuforums.org/showthread.php?t=395937](http://ubuntuforums.org/showthread.php?t=395937)

thanks for your contribution, but i should probably menion that malwarebytes, avg, microsoft security and formating all failed. i think that it may be a bootsector thing. i will have to completely restore my device to clean, thanks cofeecat though

---

### Post by coffeecat on 2011-07-09
> **javajames97 said:**
> Thank you, that is very helpfull, i assume that the shred command (with that format) will overwrite everything, including the MBR?

It will overwrite everything from beginning to end of the disc except any bad sectors (if present) that have been isolated by the hard drive firmware.

It will probably take an hour or so for a 160GB drive, so the earlier poster's suggestion of a coffee - or even a meal - might be a good idea. :wink: If this is your main sda drive we're talking about this will, of course, remove Ubuntu as well, so you can run the shred command from the live CD/USB.

---

### Post by westie457 on 2011-07-09
> **javajames97 said:**
> thanks for your contribution, but i should probably menion that malwarebytes, avg, microsoft security and formating all failed. i think that it may be a bootsector thing. i will have to completely restore my device to clean, thanks cofeecat though

I know a very little bit about boot-sector infections. That is why 'Superantispyware' was mentioned first. It installs and runs while Windows is running in Safe Mode before the boot sector and mbr are read.

---

### Post by javajames97 on 2011-07-10
> **westie457 said:**
> It installs and runs while Windows is running in Safe Mode before the boot sector and mbr are read.

how? how can anything running off the HDD install before boot sector and MBR run, thats the point of them, they are in a set place to ensure that the BIOS can set things going

Anyhow, i overwrote everything with shred and have successfully  rienstalled windows and ubuntu and, so far, everything works

---

### Post by Ad@m on 2011-07-10
> **westie457 said:**
> I know a very little bit about boot-sector infections. That is why 'Superantispyware' was mentioned first. It installs and runs while Windows is running in Safe Mode before the boot sector and mbr are read.

[http://en.wikipedia.org/wiki/Master_boot_record#System_bootstrapping](http://en.wikipedia.org/wiki/Master_boot_record#System_bootstrapping)

---

### Post by javajames97 on 2011-07-10
just out of interest, how large is the MBR (i copied 512 bytes of it, but i have read somewhere that this is not true.) What is the difference between the bootsect and MBR? and where is the bootsector?

EDIT: stupid question, wiki tells me the MBR is all inclusive and is a form of program found in the bootsect

---

