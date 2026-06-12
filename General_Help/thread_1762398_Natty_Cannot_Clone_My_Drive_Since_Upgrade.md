---
title: "Natty: Cannot Clone My Drive Since Upgrade"
date: 2011-05-19
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-19
Hello,

I have not been able to clone my drive since the upgrade to Natty.  This was never a problem for me in 'any' previous distro.

I have a dual boot Windows 7/Natty system; and I never have a problem with the Windows partition getting cloned. [COLOR=Blue]***partclone***[/COLOR] (Clonezilla) crashes about an hour and 15 min into the cloning of the Ubuntu partition.  I'm getting a ***"buffer-overflow"*** error.  I'm using ***clonezilla-live-1.2.5-35-amd64***; and have been since Lucid.  I've recently downloaded ***clonezilla-live-1.2.8-42-amd64.iso*** and am burning it to DVD now.  I don't know if this is going to help; but I'm ready to try anything; [COLOR=Blue]***as this is my only means of disaster recovery!!!***[/COLOR]

During the reboot into Natty, I received some error messasges stating that there were ***inode*** problems.  I don't know if this was on the source or destination drive; as I still had the destination drive connected to my USB port.  Then I started thinking...  What package, that wasn't there in Maverick, that **is** present in Natty ***messes with inodes???***

Then I thought [COLOR=Blue]***ZeitGeist...***[/COLOR]  So I ripped it and everything connected to it out-by-roots and tried running Clonezilla again; but no luck...

[COLOR=Blue]***Has anyone else had this problem; and what can I do about it:confused:***[/COLOR]

I've replaced all of the relevant hardware; and two days and $500 later, I still don't have a solution...

[IMG]http://1.bp.blogspot.com/_Z8u8O5UBGHc/SbrGXYTP5FI/AAAAAAAACh0/FlDIDHIMAaI/s320/pound_sign.png[/IMG]




**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-19
Well,

I've tired the cloning process with ***clonezilla-live-1.2.8-42; ***and it hangs when trying to calculate the bitmap.  I goes from 5:00:00 to 23:59:00 to go; and just waffles in this loop forever, without calculating the bitmap.

**Comments:** 




[COLOR=Blue][B]
Thanks Hannibal[/B][/COLOR]

---

### Post by lmarmisa on 2011-05-19
Try to repair the Ubuntu partition. Use a Ubuntu Live CD because the partition can not be mounted during the repair procedure.

The basic command to use is

```

sudo fsck.ext4 -f /dev/partitiontorepair

```

Append to fsck the type of partition (for example, ext4). You can see the type of the different partitions with this other command:

```

sudo parted -l

```

---

### Post by coljohnhannibalsmith on 2011-05-19
Thanks for the reply,

I already tried this by booting into the Live CD and using Gparted; and that didn't work.

So, now I'll try the command line...





**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-19
Well,

I tried the command line ***fsck*** and found no errors on either the source or destination drives. The amd64 version of Clonezilla was a dud; so I used the i686 version instead.  It worked properly; but the cloneing process failed in the same place again. So here's my theory:

In addition to a new OS; the other thing that's different is that my drive is almost full.  Since I was getting ***Buffer Overflow*** errors and now ***UDMA*** errors, I suspect that partclone is using the empty space on the partition being cloned as a data-buufer of some kind; so now I'm in the process of freeing up some space on the offending partition.  Since I have to get some work done, I'm not going to try this again until bed time.





**Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-19
Well,

It failed in the same place with new hardware & a new Clonezilla version.  It looks like I'm gonna hafta get different cloning software.

Can anyone recommend a replacement for Clonezilla???






**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-20
Aside from Clonezilla,

[COLOR=Blue]***What other HDD partition cloning tools are there; and which are the best???***[/COLOR]

I'd prefer one with a bootable image...





**Thanks Hanibal**

---

### Post by linuxinstalledfromhdd on 2011-05-20
Just a recommendation... Try remastersys maybe.  I've never had a problem with making viable clones of my Ubuntu installations with it. Tested it in Natty, and had no problems.

---

### Post by coljohnhannibalsmith on 2011-05-21
Thanks for the reply,

I've researched Remastersys:

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

and it does two things:

[SIZE=4][COLOR=#000099]**What is remastersys?**[/COLOR][/SIZE] [LEFT][COLOR=#000099]**Remastersys**[/COLOR] is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.[/LEFT]
  
[LIST]
[*]It can make a full system backup including personal data to a ***live cd or dvd*** that you can use anywhere and install.
[*]It can make a distributable copy you can share with friends.  ***[COLOR=Blue]This will not have any of your personal user data in it.[/COLOR]***
[/LIST]
***This appears to be a very useful tool; but I need an app that will 'clone' my entire HDD to another HDD, which this app will not do.***

Thanks for the effort.




[COLOR=Blue]**Hannibal**[/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-22
Well,

I moved hardware around again and decided I'd give Clonezilla another try; and the cloning process failed in the same place again.  When it failed it reported inode problems again; but this time I let it take as long as it wanted to to fix them; and it eventually finished.  It also properly resized both partitions to fit the larger drive.  I must say, I was very surprized indeed.  And now since I have my boot order setup correctly to allow booting from an external drive, I decided to let it try to boot; and it did indeed try.  I was surprized by this; but I was surprized even more by the fact that a ***different*** version of GRUB was installed on the destination drive.

The version of GRUB on the source drive is 1.98.xxxxx something.  It's probably the latest version of GRUB before 1.99.  But, to my surprize GRUB 1.99 was installed on the destination drive; and instead of booting, it greeted me with the following message:

[COLOR=Blue][B]Welcome to GRUB:
GRUB>[/B][/COLOR]

and just sat there waiting for input...

What I'd like to know is...  why did Clonezilla install GRUB 1.99, when I instructed it to 'copy' the boot loader from the source drive???  And why did Clonezilla have to repair inodes at all.  This was not necessary in Maverick or Lucid; and I haven't changed the filesystem from ext4:confused:  Also in its present condidtion GRUB won't boot...

[COLOR=Blue]***Is there a way to get the version of GRUB installed on the destination drive to build a menu and start; or better yet to to get Clonezilla to obey my order to 'copy' the boot loader from the source drive***[/COLOR]:confused::confused:  ***And what about all this inode business***:confused::confused::confused:





**Thanks Hannibal**

---

### Post by slooksterpsv on 2011-05-22
Wait won't dd work?

dd if=/dev/sda of=/dev/hda bs=16384 conv=notrunc,noerror

or just:

dd if=/dev/sda of=/dev/hda

where sda and hda are respective to the drive/partitions you want to "clone"

---

### Post by coljohnhannibalsmith on 2011-05-22
> **slooksterpsv said:**
> Wait won't dd work?

dd if=/dev/sda of=/dev/hda bs=16384 conv=notrunc,noerror

or just:

dd if=/dev/sda of=/dev/hda

where sda and hda are respective to the drive/partitions you want to "clone"

Hmmm... I've really been giving dd some thought. I'm an former Windows user and I prefer not to use the command line if I can avoid it, especially for something as complicated as cloning. I have a dual-boot config. Do you think dd can handle it??? 
 
Do I clone one partition at a time or will it do the whole thing at once??? 
 
Also I've included some screenshots of my partition-table from GParted and have found what appears to be an error on my Windows/Boot partition... 
 
**Comments: **
 
 
 
 
 
[B]Hannibal
[/B]

---

### Post by slooksterpsv on 2011-05-22
dd will clone it fully.

If you specify:

dd if=/dev/sda of=/dev/sdb

that will copy everything, even the bootloader.

---

### Post by linuxinstalledfromhdd on 2011-05-22
If you don't want to use the command line, then you are going need to install and try something like remastersys..  I use it all the time for cloning.  You never have to use the command line with it, except to install it perhaps.

---

### Post by coljohnhannibalsmith on 2011-05-22
Well,

It appears that the current version of Clonezilla does indeed replace GRUB 1.98.xxxxx with 1.99.xxx  by default.  God this is an annoying behavior; and as far as I know can't be turned off.  I think the decision on wether or 'not' to upgrade GRUB should be mine & mine only!!!  I want my cloning software to just copy what's there and 'not' make 'any' editorial decisions on it's own...  So I've downloaded an older version that I believe predates the release of GRUB 1.99.xxxxx.

I was also able to use **chkdsk /f** to repair the Windows 7 partition and I also made sure that both file systems were in tip-top shape, by performing a 'check' with GParted.  Yet I'm still having the same problem when copying the Ubuntu partition and in the same place...

I've attached some JPGs, so that you can see the error messages on my screen from the failure; and I've also provided a link to a YouTube video of Clonezilla actually failing on my system.  BTW, I used the **--rescue** option; and the cloning process finally finished; and the destination drive actually booted and functioned normally.

[http://www.youtube.com/watch?v=mdZXwlxcDow](http://www.youtube.com/watch?v=mdZXwlxcDow)

I've also documented two bad memory cells in my unit; and attached an image of it.  These cells have always been bad; and so far have not impaired the operation of my system, or ever prevented me from cloning; but I've inlcluded the image just in case...





**Hannibal**

---

### Post by linuxinstalledfromhdd on 2011-05-22
That definitely would be annoying.  Remastersys will create a live bootable clone of your system that will install itself to your new system. Works like a restoration disc. Also works as a live custom bootable USB drive and will install your custom restoration onto like architecture.  And I use a bash script to pull anything larger than the 4.7gb disc will fit.

---

### Post by WasMeHere on 2011-07-25
This thread is interesting for me. At home I am using Lucid as a 'work-horse' and I am testing various Linux versions including Natty. I have stayed with ext3 until recently, when I wanted to evaluate the speed of ext4 to give an old P4-2.8GHz Dell a second chance.

Indeed Lucid is fast with ext4, so I want to keep it, but before a general upgrade, I want to have complete and reliable backup. Since 2008 I have used dd to get a first and total image and PING to make images of the partitions approximately once every month. But PING cannot manage ext4 in an efficient way (it can only image everything including the free space).

So I am trying Clonezilla with Partclone. I downloaded 'clonezilla-live-1.2.8-46-i686.iso', made a CD-rom and was successful at once, and faster than PING. The test computer has one NTFS partition with WinXP and one extended partition with Lucid + a swap partition. Since I had a dd | gzip image, I dared to restore from the Clonezilla image to the computer system disk. It works well after that, I have not found any error. Grub works, WinXP works and Lucid works. I guess the partitions are identical. I have not checked if the grub version has changed, but it works as before anyway.

Maybe the problem you describe, coljohnhannibalsmith, is because you have some **bad sectors (physical errors) on your disk**, and the current version of Clonezilla cannot handle it. I don't like disk errors, so I try to rescue everything (using ddrescue) to a good disk, at least for system disks or disks on my workhorse. **Try ddrescue**, the manual is very helpful (compared to other linux info pages)!

But I realize that disks can get some bad sectors early and then survive for years, so **I suggest to ask the developing team of Clonezilla or Partclone to test and if necessary improve cloning disks with bad sectors. The first step could be to identify the problem and give advice what to do directly on the screen**.

---

### Post by WasMeHere on 2011-07-25
I was curious, so I looked at the Clonezilla forum, and I found this text:
> #
mrvideo

2010-09-16 06:43:31 CEST
I'm using the latest version, amd64 ISO build. I have a laptop 100GB SATA drive that I'm trying to clone and even though I enabled the -rescue option, it refuses to get past the first bad sector that it hit. I had to clone a different drive last night and it got past the sector errors that it hit. Add. Sense: Unrecovered read error - auto reallocate failed I went through the process of running the XP chkdsk on the drive and managed to get it to repair, but I still can't get past this sector. I can access the HDD just fine under XP, but it obviously has issues. What next? Am I screwed?
#
steven_shiauProject AdminAccepting Donations

2010-09-19 09:37:40 CEST
The rescue function of partclone is not as good as ddrescue or gddrescue. Therefore you'd better to try ddrescue or gddrescue. These two packages are available in Clonezilla live, too. Steven.
#
mrvideo

2010-09-20 06:26:38 CEST
I did a search on clonzilla.org and got zero hits for ddrescue. I did not see any reference to ddrescue in the live doc web page. So, I am cluless as to where to find it within clonezilla live. How do you tell the program, once it has been booted (I used a CD) to use ddrescue instead of partclone?
#
mrvideo

2010-09-20 09:51:55 CEST
From digging into the live architecture, it is Linux afterall :-) I found the program and it seems that I have to run it manually as the main program doesn't have an option to use it instead, at least not that I've noticed. I have it running and it is getting past the bad areas. It is going to take a while, but it should do the job. Thanks.
#
mrvideo

2010-09-20 13:50:04 CEST
Final post. Drive is up and running. The laptop is working again. Thanks for the tip about ddrescue, that did the trick.
#
steven_shiauProject AdminAccepting Donations

2010-09-22 16:03:11 CEST
No problem. Enjoy! Steven.


So, even 'Mr Clonezilla himself' recommends ddrescue to clone disks with bad sectors. And it is on his live disk. You can also use it from a live ubuntu disk after installation:

sudo apt-get install ddrescue

info ddrescue
1. read the all the info pages about ddrescue
2. take your time to understand, start from a suitable example
3. copy (clone) as much as possible to another disk (if your data is outside the bad sectors, the cloned disk should be what you want)

---

