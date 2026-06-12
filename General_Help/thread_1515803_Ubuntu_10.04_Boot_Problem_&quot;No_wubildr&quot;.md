---
title: "Ubuntu 10.04 Boot Problem &quot;No wubildr&quot;"
date: 2010-06-22
forum: General Help
---

### Post by v1gorus on 2010-06-22
Hi, I'm having this problem and need it fixed soon. I have Win7 then installed wubi with Ubuntu 9.10 then recently I updated to 10.04. Everything was ok until one day I boot into Win7 for something and I can't get back into Ubuntu. It flashes me the error:
Try (hd0,0): FAT32 : No WUBILDR
Try (hd0,1): NTFS5: No wubildr
Then restarts. I've searched for solutions and found similar and same problems but no solution. I checked in C:/ and C:/ubuntu/winboot and it does have the wubildr file. I am running on a ASUS U81A laptop if that helps.

---

### Post by v1gorus on 2010-06-22
I get this when I tap insert at post.
```
hard drives: 1, int13:F0008090, int15:F000F859
get_diskinfo(80), int13/41(80), version=AA300005, int13/48(80), err=0, C/H/S=16/383/16/63, sector count/size=2344416480/0, int13/08(80), version=0, C/H/S=1024/171/40, int13/02(80), err=0,
warning: MBR cylinders(14594) is not equal to the BIOS one (16383)

warning: MBR heads(255) is not equal to the BIOS one (171)

warning: MBR total sectors(234452610) is greater than the BIOS one (234441648 )
some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.
LBA, C/H/S=14594/255/63, sector count/size=234452610/512
boot drive=80, int13/4B01(80), err=1, drive=80, not CD
get_cdinfo(7F), int13/4B01(7F), err=1, drive=7F, cdrom_drive==FFFFFFFF
starting cmain() ... open/default ... failure 			 		
```

---

### Post by v1gorus on 2010-06-23
I also tried today to replace wubildr in c:/ with a newer version. still didn't work.

---

### Post by bcbc on 2010-06-23
Copy the root.disk file to somewhere safe. it's in c:\ubuntu\disks\, and wherever you copy it, make it outside that directory.

Then you can try uninstalling and reinstalling wubi. After it's completed, just copy over the new root.disk file with your backup. Assuming it's just your wubildr that's not working properly, this will get you back in to your old install.

The root.disk file is a virtual disk for ubuntu and contains all your data/apps/settings. If nothing is wrong with it, this method will work. If the above method did not work, you still have all your data backed up and accessible.

You can mount this file (using the '-o loop' option) and pull off important data, e.g. from the live CD if for some reason the above doesn't work.

See wubi guide for more info. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by v1gorus on 2010-06-23
i am running live cd right now and can;t find my files.

---

### Post by bcbc on 2010-06-23
If you're on live cd you first have to mount your hard drive. You should be able to do this by clicking on the drive icon on your desktop or manually if you prefer.

If it's automatic it will be mounted under /media/xxx where xxx is either the drive label or the UUID. (the uuid is ugly but type the first letter/number and press TAB and it auto completes)

Then mount your root.disk as follows:
```
sudo mount -o loop /media/*xxx*/ubuntu/disks/root.disk /mnt
```

Then to see your ubuntu install you can ```
nautilus /mnt
```
Your data will be under /mnt/home/<username>

---

### Post by v1gorus on 2010-06-23
it work i recovered my files. now i need to either fix this damn wubildr or erase everything all together(either ubuntu/wubi or everything).

p.s where is my theme located?

---

### Post by wilee-nilee on 2010-06-24
Post the boot script in my sig in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
This way we and bcbc will see the whole setup.

---

### Post by bcbc on 2010-06-24
> **v1gorus said:**
> it work i recovered my files. now i need to either fix this damn wubildr or erase everything all together(either ubuntu/wubi or everything).

p.s where is my theme located?

I gave you a method of fixing wubi earlier. You have nothing to lose, provided you back up the root.disk somewhere outside of c:\ubuntu before uninstalling (or it will be gone for good).

If you have all your important data from the broken wubi, I'd recommend just doing a fresh install, preferably direct to partition (non-wubi). 

If you want to install to partition, use the Windows 7 disk manager to shrink your windows partition and create a new space into which you can install directly. 

PS I'll look at the bootinfoscript results if you post them and see if something jumps out.

PPS what theme are you referring to?

---

### Post by v1gorus on 2010-06-24
I did recover my root.disk. I uninstalled ubuntu thu win7. im downloadin ubuntu 10.04 x64 atm. x64 is the way to go with a x64 cpu right. im planning on making another partition or getting rid of everything and having soley ubuntu on my laptop in that a smart choice for a nub like me. 

crap should of told me about that boot script before i uninstall ubuntu.

---

### Post by wilee-nilee on 2010-06-24
> **v1gorus said:**
> I did recover my root.disk. I uninstalled ubuntu thu win7. im downloadin ubuntu 10.04 x64 atm. x64 is the way to go with a x64 cpu right. im planning on making another partition or getting rid of everything and having soley ubuntu on my laptop in that a smart choice for a nub like me. 

crap should of told me about that boot script before i uninstall ubuntu.

First I will say bcbc knows their way around boot problems and wubi:p

Second I would keep W7 you never know when it may come in handy, especially if it is the OEM, if you have a install DVD though do what works. A dual boot is easy as wubi is you just have to have your ducks in a row.

---

### Post by bcbc on 2010-06-24
the bootinfoscript is not a 'silver bullet'. It does provide a good picture of what's installed on the computer. I said I'd look at it if you went to the trouble of producing it. But it doesn't have good diagnostics on wubildr so... I didn't think it would help in your case.

In any case, you are better off going for a new install (wubi is always a temporary solution), and you have your data, so... :)

+1 on wilee-nilee's comment. Don't remove windows until you have everything working well. It's easier to leave it and run a dual boot, than to delete it and find out that you need it later.

---

### Post by v1gorus on 2010-06-24
I uninstalled wubi and ubuntu. i installed ubuntu 10.04 on another partition. i saved the root.disk. how do i set my root.disk in my ubuntu.

---

### Post by v1gorus on 2010-06-24
do i mount the root.disk like before?

---

### Post by Justin_West on 2010-06-25
> **bcbc said:**
> Copy the root.disk file to somewhere safe. it's in c:\ubuntu\disks\, and wherever you copy it, make it outside that directory.

Then you can try uninstalling and reinstalling wubi. After it's completed, just copy over the new root.disk file with your backup. Assuming it's just your wubildr that's not working properly, this will get you back in to your old install.

The root.disk file is a virtual disk for ubuntu and contains all your data/apps/settings. If nothing is wrong with it, this method will work. If the above method did not work, you still have all your data backed up and accessible.

You can mount this file (using the '-o loop' option) and pull off important data, e.g. from the live CD if for some reason the above doesn't work.

See wubi guide for more info. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I'm about to try this method, but what I want to know is, once I reinstall wubi and run the automatic updates and all, will it crash again?  Has this issue been fixed?  This is the second time this has happened.

---

### Post by bcbc on 2010-06-25
> **v1gorus said:**
> do i mount the root.disk like before?

Yes - exactly the same as you did from the live CD.

---

### Post by bcbc on 2010-06-25
> **Justin_West said:**
> I'm about to try this method, but what I want to know is, once I reinstall wubi and run the automatic updates and all, will it crash again?  Has this issue been fixed?  This is the second time this has happened.

I had a few 'crashes' after running updates on 10.04. If your ubuntu is crashing during the boot process, then the method I described will not help - as your problem is on the root.disk itself. The method shown was if you had a 'good' root.disk backup, and then the current root.disk is corrupted or if the wubildr (grub4dos) stopped working. Once your root.disk isn't working, this method doesn't help.

So, do you get a menu still? Can you boot from an older kernel or in rescue mode? You need to describe in more detail what your problem is. 

Please create a new thread for yourself, and then just edit your previous post with a link to it.

---

### Post by 10dollarNOOBIE on 2010-06-25
how can i delete Ubuntu leftover in my boot menu?
it goes like this:


Windows Vista
Ubuntu         <------this 1 is 9.10
Ubuntu         <------this is 10.04

how can i delete 9.10 w/o using my vista cd to repair it because my sister lost it. i dont think its a serious problem though but i want to get rid of it. Pls help me if theres any other ways to delete it, i installed ubuntu 9.10 via wubi then 10.04 was released i downloaded 10.04 than updating because i just want to install it using wubi. i tried uninstalling wubi but that 9.10 is still there.



LOVE LOVE LOVE

---

### Post by bcbc on 2010-06-25
> **10dollarNOOBIE said:**
> how can i delete Ubuntu leftover in my boot menu?
it goes like this:


Windows Vista
Ubuntu         <------this 1 is 9.10
Ubuntu         <------this is 10.04

how can i delete 9.10 w/o using my vista cd to repair it because my sister lost it. i dont think its a serious problem though but i want to get rid of it. Pls help me if theres any other ways to delete it, i installed ubuntu 9.10 via wubi then 10.04 was released i downloaded 10.04 than updating because i just want to install it using wubi. i tried uninstalling wubi but that 9.10 is still there.



LOVE LOVE LOVE
see this section of the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?").

---

