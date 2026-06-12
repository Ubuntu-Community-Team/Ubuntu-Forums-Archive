---
title: "Recently converted to Ubuntu"
date: 2011-03-10
forum: General Help
---

### Post by dundy4 on 2011-03-10
Hello all,

Clearly from my post count I'm brand new to this forum, however hopefully not long.
My friend quite literally hours ago converted me to Ubuntu from 7, I have some intermediate knowledge having come from an avid FTP user and etcetera. I was simply curious as if there was an "absolute beginner" reference guide for getting around things like the terminals, to my surprise Google has shown no help. 

I was ALSO wondering if anybody would be able to direct me as to where I can find out how turn my apparently dual partitioned Ubuntu/7 into simply Ubuntu, as it never allowed me to opt out of it when installing :(

Thanks!

Edit: And already I can see I posted this in the wrong section... Whoops!

---

### Post by kc1di on 2011-03-10
Here's a link to an online guide that may be of help. and you can always ask on the forum if you run into difficulty.
[http://ubuntuguide.org/wiki/Ubuntu:Maverick]("http://ubuntuguide.org/wiki/Ubuntu:Maverick")

Enjoy

---

### Post by HermanAB on 2011-03-10
Howdy,

Welcome!

[http://google.com/linux](http://google.com/linux)

[http://tldp.org](http://tldp.org)

---

### Post by coffeecat on 2011-03-10
Welcome to the forum. :)

> **dundy4 said:**
> I was ALSO wondering if anybody would be able to direct me as to where I can find out how turn my apparently dual partitioned Ubuntu/7 into simply Ubuntu, as it never allowed me to opt out of it when installing :(

Are you sure? I'm sure there's "use whole drive" option in the installer. Indeed there's horrible design flaw in the 10.10 installer where if you choose the "install alongside" option (to get a dual-boot) you have a good chance of wiping out your Windows partition(s). Did you perhaps do a wubi installation? Wubi:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you did a wubi install, then Ubuntu goes onto a virtual HD within your Windows partition and clearly you can't have Ubuntu without Windows in this situation.

Also - are you sure you want to get rid of Windows? Most people would advise hanging on to Windows until you have more experience of Ubuntu. Anyway, open a terminal (Applications > Accessories) and post the output of this command:

```
sudo fdisk -lu
```That will tell us a little of your setup and we can take it from there. You will be asked for your password - yes, it is going in even though you are given no visual feedback. Please post the output between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon in the message toolbar for this.

---

### Post by mastablasta on 2011-03-10
> **dundy4 said:**
> Hello all,
 
Clearly from my post count I'm brand new to this forum, however hopefully not long.
My friend quite literally hours ago converted me to Ubuntu from 7, I have some intermediate knowledge having come from an avid FTP user and etcetera. I was simply curious as if there was an "absolute beginner" reference guide for getting around things like the terminals, to my surprise Google has shown no help. 

Ubuntu manual and then linuxcommand.org - both free e-books are a good read. 
 
> 
I was ALSO wondering if anybody would be able to direct me as to where I can find out how turn my apparently dual partitioned Ubuntu/7 into simply Ubuntu, as it never allowed me to opt out of it when installing :(
 
 
two options.
 
1. boot from live CD, run gparted from terminal, delete windows partition (format as linux ) and then update grub
2. simply boot from liveCD, run gparted, delete all partitions, reinstall ubuntu using the whole disk for instal.
 
if you have a working Win7 you might keep it for a while just in case. also make sure oyu dont' have wubi install, because of you do you will need a different procedure.

---

### Post by dundy4 on 2011-03-10
> **coffeecat said:**
> Welcome to the forum. :smile:



Are you sure? I'm sure there's "use whole drive" option in the  installer. Indeed there's horrible design flaw in the 10.10 installer  where if you choose the "install alongside" option (to get a dual-boot)  you have a good chance of wiping out your Windows partition(s).


Thank you! 
Yes, it was a wubi installation and I actually had a problem going into  the installation that when i went to restart it and run, it gave me a potentially  corrupt file or missing file error of some sort (I can give you the  exact reference if you need, cellphone imaged it for such an occasion.),  to which I fixed later on and it just skipped a bunch of installation  stuff I can bet you.


> **coffeecat said:**
> 
Also - are you sure you want to get rid of Windows? Most people would  advise hanging on to Windows until you have more experience of Ubuntu. 

Well, the friend who converted me is actively there to assist me with  any real problems necessary, hell he did have me setup ssh just for  helping me get my appropriate drivers upgraded cause I did it wrong. As  for getting rid of Windows, I guess I should've reworded that, I would  like to make Ubuntu my MAIN partition, I only currently have I believe  25 gigs of maximum usable space, which is where Windows conflicted  saying I couldn't use any more.

Using the command you gave me this is the output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa40bc8d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   465917951   232957952    7  HPFS/NTFS
/dev/sda2       465917952   488390655    11236352    7  HPFS/NTFS

I am hoping that is all correct because my guessing nature cannot make chicken scratch.

---

### Post by Rushyang on 2011-03-10
There is [ubuntu pocket guide]("http://www.ubuntux.org/ubuntu-pocket-guide-and-reference-ebook-free-as-in-beer") available on the internet for totally free.. You should have a look at once for all basic understanding..

---

### Post by coffeecat on 2011-03-10
> **dundy4 said:**
> Yes, it was a wubi installation

....

I only currently have I believe  25 gigs of maximum usable space, which is where Windows conflicted  saying I couldn't use any more.

I think that may be a limitation of wubi rather than Windows, but tbh I have only limited experience of wubi. Wubi is really only designed as a try out platform. It has its limitations and disadvantages. If you look in C:\ubuntu while in Windows, you will find a number of files, one of which is the virtual Ubuntu hard drive. I can't remember what it's called. I think you will find that will be 25GB, and it's a major operation enlarging it. 

> **dundy4 said:**
>  Using the command you gave me this is the output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa40bc8d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   465917951   232957952    7  HPFS/NTFS
/dev/sda2       465917952   488390655    11236352    7  HPFS/NTFS


You have two NTFS partitions, NTFS being a Microsoft filesystem. Partition #1 is the bootable one and is 238.5GB in size. That is probably your Windows C: partition. Partition #2 is 11.5GB. Which is interesting. Partition #2 is about the right size for a manufacturer's restore partition but pre-installed Windows 7 usually comes with another boot partition of about 100MB. Is this an OEM installed system or did you install Windows 7 yourself from a Microsoft DVD?

If you really, really, really, really want to blow Windows 7 away, then it's very easy. You simply burn a CD from the downloaded Ubuntu ISO, boot up with the CD and choose the "use whole drive" option in the installer. But, personally, I wouldn't do that.

One alternative, if that sda2 partition is a restore partition, would be to reduce the size of the Windows 7 partition from within Windows itself, and then use the Ubuntu live CD to create partitions with Linux filesystems in the resultant freed space, after which you would install Ubuntu to the new partitions. This would result in a "proper" dual-boot and you could get rid of the wubi install. 

Have a think about what you want to do and then I and/or others can help you with whatever you choose.

---

### Post by dundy4 on 2011-03-10
> **coffeecat said:**
> 
You have two NTFS partitions, NTFS being a Microsoft filesystem. Partition #1 is the bootable one and is 238.5GB in size. That is probably your Windows C: partition. Partition #2 is 11.5GB. Which is interesting. Partition #2 is about the right size for a manufacturer's restore partition but pre-installed Windows 7 usually comes with another boot partition of about 100MB. [B]Is this an OEM installed system or did you install Windows 7 yourself from a Microsoft DVD?

[/B]Sad story here but it's actually torrented, it originally came preinstalled with vista, and that is why I'd like to make ubuntu my main OS so i can load vista back up on it and not be using it every god damn day.

> **coffeecat said:**
> 
If you really, really, really, really want to blow Windows 7 away, then it's very easy. You simply burn a CD from the downloaded Ubuntu ISO, boot up with the CD and choose the "use whole drive" option in the installer. But, personally, I wouldn't do that.

One alternative, if that **sda2 partition is a restore partition**, would be to reduce the size of the Windows 7 partition from within Windows itself, and then use the Ubuntu live CD to create partitions with Linux filesystems in the resultant freed space, after which you would install Ubuntu to the new partitions. This would result in a "proper" dual-boot and you could get rid of the wubi install. 


That would be correct.

As I mentioned before, even if its just making Ubuntu take a majority of the partition so I can install vista back up and say to hell with it now and again, that's fine!

---

