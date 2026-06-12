---
title: "Changed partition type, computer won't boot. &quot;GRUB Error 17&quot;"
date: 2009-11-09
forum: General Help
---

### Post by Esoteric.caek on 2009-11-09
I am currently typing this from my parents' computer. 

_**TL;DR:**_ I accidentally changed my main, important partition to "linux extended" and after I restarted the computer to see if I could still boot vista, it only gives me: 
"GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17"
after trying to boot ubuntu with a disc and foolishly losing all data on my flash drive to try to boot from that, it insists on giving me that error.

_Whole story:_
     I created a 30 GB partition for Ubuntu months ago and upgraded to 9.1 last night on my own computer without any problems. I got the driver for my new GPU going, cranked up the settings, and installed all the updates I could. Everything went fine with the installation. 

     Today, however, I decided to be a moron and mess around with Ubuntu's disk utility. I was wiping a useless (to me) 10 GB partition through Ubuntu's Disk Utility and planned on changing it to the type "Linux Extended". What I did, though... TOTALLY by accident, is change my MAIN partition to linux extended. I wasn't paying attention, I suppose.  

     I have one 400 GB harddrive in my case. It's made up of a large (the main) partition dedicated to Vista[ids] and another large partition for my music. I don't use Ubuntu often, so everything important and all was on the vista one. My programs, documents, pictures, etc. Whatever, though.

     Thing is, I tried to change it right back. But.. it was error message after error message. Ubuntu was still running fine and everything, but I couldn't change that partition back to NFTS or FAT32 or whatever it'd been. 

     I restarted my computer to try to change the type back, and nothing will boot. I tried booting Ubuntu with a disc and my flash drive to no avail. It's the same error every time:
"GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17"
I did mess with the BIOS a bit as suggested on other forums, but maybe I didn't try everything.

    I dunno. Help would be **greatly** appreciated. =]

---

### Post by jbrown96 on 2009-11-09
Boot the Ubuntu liveCD and post the output of the following ```
sudo fdisk -l
```

---

### Post by Aemaeth on 2009-11-09
Ok this may be a long shot and I have not tested it but its worth a try at this stage in the game...

boot the live cd of ubuntu 9.04 or 9.10 and open a terminal then type

# sudo apt-get install ntfsprogs and gparted

then 

# sudo gparted

this will launch gparted with admin rights, then try switching the partition type back to NTFS. warning again this is just an idea. (but if you are up a creek then its worth a try)

Good luck!

---

### Post by Esoteric.caek on 2009-11-09
Thank you both, jbrown and aemaeth, for responding so promptly. The issue here is.. nothing will boot. I'll try to boot from another CD, but if that doesn't work I have no idea what to do. D:

---

### Post by jbrown96 on 2009-11-09
> **Aemaeth said:**
> Ok this may be a long shot and I have not tested it but its worth a try at this stage in the game...

boot the live cd of ubuntu 9.04 or 9.10 and open a terminal then type

# sudo apt-get install ntfsprogs and gparted

then 

# sudo gparted

this will launch gparted with admin rights, then try switching the partition type back to NTFS. warning again this is just an idea. (but if you are up a creek then its worth a try)

Good luck!


Don't do this! 

When you create a file system it overwrites all the important locations on the disk. It will basically make it impossible to recover. The only hope is that an extended partition did not overwrite much since it's basically just a container file system. 

You really don't want to make any changes to this disk. It would be best if you have another drive of equal or greater size that you can make a copy with. Almost anything that could recover from this problem has the ability to make things even worse.

---

### Post by jbrown96 on 2009-11-09
> **Esoteric.caek said:**
> Thank you both, jbrown and aemaeth, for responding so promptly. The issue here is.. nothing will boot. I'll try to boot from another CD, but if that doesn't work I have no idea what to do. D:

Why can't you boot from a CD?

---

### Post by Esoteric.caek on 2009-11-09
> **jbrown96 said:**
> Why can't you boot from a CD?
I'm not sure. I may have downloaded the wrong ISO the first time. There's a special one for CDs, isn't there? If so, I downloaded it and I'm about to burn it.

---

### Post by jbrown96 on 2009-11-10
Just make sure when you burn it that you burn it as an image. You can't just add the .iso file to the cd. This means you can't use the Windows burning application. You will need something like Nero. There is a popular free app, but I can't remember the name. Alcohol120???

Here's the directions
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Esoteric.caek on 2009-11-10
Oh, I have Nero on my computer on windows but my parents conveniently have Ubuntu, hahah. I'll just use its "write to disc" function or however it's explaining it in this tutorial.
I'm fairly new to Ubuntu still =/

---

### Post by jbrown96 on 2009-11-10
Just use the disk burning app. It's pretty obvious how to do it in Ubuntu.

Don't make any changes to your hard drive until we know what's going on with it any better. 

It's almost certain that you won't be able to use that for Windows anymore. We're really at the stage where we are just hoping to get some of your data back. You're going to have to reinstall windows, because some of the data will be overwritten.

---

### Post by Esoteric.caek on 2009-11-10
Ah! It booted! The first steps of progress in over 6 hours. It took me an extra 2 or so to clear my BIOS password I'd set and forgotten. lmao. 
I'll post the info I gather asap

---

### Post by Esoteric.caek on 2009-11-10
Here's the output:

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Ignoring extra extended partition 4

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2254cdfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       24975   190378282+  85  Linux extended
/dev/sda3           24976       44836   159533482+   7  HPFS/NTFS
/dev/sda4           44837       48641    30563662+   5  Extended
/dev/sda5   ?        1684      121065   958924038+  70  DiskSecure Multi-Boot
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

The second drive is the drive I accidentally converted, as you can most likely assume. So.. what now? =/

---

### Post by Esoteric.caek on 2009-11-10
Halp ;_;

---

### Post by jbrown96 on 2009-11-10
Here's what you need to do.
1) backup your partition table ```
sudo dd if=/devsda of=Desktop/partition-table.txt bs=512 count=1
``` This will put a file on your desktop. Save this file somewhere safe. 
2) You really should backup the entire drive, but you will need one with as much free space as this entire drive is. Going to assume that you won't be able to do this.
3) Open gparted and figure out exactly how big your broken NTFS partition is. You need the exact MB where it starts and ends.
4) try to change the partition back. Hopefully this will work. ```
sudo parted /dev/sda mkpart primary ntfs START END
``` replace START and END with what you found in #3. 
5) You did save that table somewhere right!!
6) Reboot and see if it works.

---

### Post by Esoteric.caek on 2009-11-10
I'll try all this now. I'm using the Gparted that is found in ubuntu, right?

---

### Post by Esoteric.caek on 2009-11-10
> **jbrown96 said:**
> Here's what you need to do.
1) backup your partition table ```
sudo dd if=/devsda of=Desktop/partition-table.txt bs=512 count=1
``` This will put a file on your desktop. Save this file somewhere safe. 
2) You really should backup the entire drive, but you will need one with as much free space as this entire drive is. Going to assume that you won't be able to do this.
3) Open gparted and figure out exactly how big your broken NTFS partition is. You need the exact MB where it starts and ends.
4) try to change the partition back. Hopefully this will work. ```
sudo parted /dev/sda mkpart primary ntfs START END
``` replace START and END with what you found in #3. 
5) You did save that table somewhere right!!
6) Reboot and see if it works.

I put in the first string of code and got this: 
"dd: opening `/devsda': No such file or directory"

I'm not sure what to do about that.

---

### Post by JKyleOKC on 2009-11-10
> **Esoteric.caek said:**
> I put in the first string of code and got this: 
"dd: opening `/devsda': No such file or directory"

I'm not sure what to do about that.There needs to be a / between the v and the s, so that it's "/dev/sda" and then it should work. This must have been a typo in the original message...

---

### Post by Esoteric.caek on 2009-11-10
> **JKyleOKC said:**
> There needs to be a / between the v and the s, so that it's "/dev/sda" and then it should work. This must have been a typo in the original message...
That worked. Thank you!
Following the rest of the instructions now..

---

### Post by Esoteric.caek on 2009-11-10
I have an external harddrive with 360 GB of free space- plenty to hold all the corrupted  drive's data. 
Should I make an image of the entire drive and put it on the external drive?

---

### Post by audiomick on 2009-11-10
> **Esoteric.caek said:**
> I have an external harddrive with 360 GB of free space- plenty to hold all the corrupted  drive's data. 
Should I make an image of the entire drive and put it on the external drive?

Hallo. First of all, my deepest sympathy...

I can't help you much with this, except for this advice

You are in a situation where maybe all is lost. If what you are trying fails, it may make things worse, so...

If you have the chance to copy the disc before you start messing around with it, do it. If all else fails, you still might be able to rescue files from the copy

good luck
Michael

---

### Post by jbrown96 on 2009-11-10
You can try to backup your partition onto the external. You need to figure out which disk is the external with ```
sudo fdisk -l
``` then run ```
sudo dd if=/dev/sda2 of=/dev/sdX
``` substitute the X. 

That was a typo in my earlier post. It should be /dev/sda. That dd command will take a long time, and it won't give you any feedback about how far along it is. Just backup your mbr and run the parted command from my earlier post.

---

### Post by Esoteric.caek on 2009-11-10
Thank you for your consistent aid, jbrown. 
I ran the "sudo dd if=/dev/sda2 of=/dev/sdf1" command and the output was this:
"ubuntu@ubuntu:~$ sudo dd if=/dev/sda2 of=/dev/sdf1
2+0 records in
2+0 records out
1024 bytes (1.0 kB) copied, 0.0149586 s, 68.5 kB/s"

Does that look correct to you..? I don't think it should say 1024 bytes. It didn't take long at all, either. D:

---

### Post by jbrown96 on 2009-11-11
It's not reading enough data, so we need to manually set what needs to be copied. This may not be accurate, but it's what you posted from fdisk earlier. ```
sudo dd if=/dev/sda of=/dev/sdf1 skip=1275 count=23700
``` I'm not sure that's large enough. Was your Vista partition really small (like 6GB)?

---

