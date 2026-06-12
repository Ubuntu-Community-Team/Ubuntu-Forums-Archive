---
title: "IBM ThinkPad"
date: 2009-11-08
forum: General Help
---

### Post by PoisonSerpent on 2009-11-08
Hi all,

I am getting an IBM ThinkPad (used obviously), with an 80GB HDD, CDRW/DVDROM drive, WiFi card, a gig of RAM, etc..

It will have XP Pro preinstalled (will not come with the XP disk), and I want to dual boot it with Ubuntu. I am planning to have the following partition layout:

20GB - NTFS - XP Pro
20GB - NTFS (or any other filesystem that will work) - Storage
38GB - ext3 - Ubuntu Filesystem
2GB - swap - Swap Partition

Would I be able to resize the XP partition to 20 gigs with GParted, and then make the 3 other partitions? Then just install Ubuntu on the ext3 and swap partitions?

It would be Ubuntu 9.10 (I believe it could handle it).

If you have any suggestions with what I should do, include it in your post.

Thanks all,

PoisonSerpent :p

---

### Post by PC_load_letter on 2009-11-08
I did this before, and on an IBM Thinkpad as well LOL :D
Just do it with the GParted LiveCD, what I did is that I resized the Windows XP partition from 40GB to 20GB and then formatted the free space to ext3. When I restarted XP the next time, it gave a message that the hdd had to be checked, the message was on a blue screen (I was quite nervous that XP won't restart), but a minute later, it said everything is fine and it restarted normally and everything was normal ever since. 

It goes without saying that the XP partition has got to be smaller than the new size, i.e. if XP is already 22GB full, you will not be able to resize it to 20GB.

---

### Post by lswb on 2009-11-08
Also, do a complete disk scan and defrag from XP before shrinking, and making a backup is advised.

---

### Post by PoisonSerpent on 2009-11-09
Just burnt the GParted Live CD. Would it be able to make a new NTFS partition? Or can it make a partition that is readable by both Ubuntu and Windows?

Thanks,

PoisonSerpent

---

### Post by alphacrucis2 on 2009-11-09
> **PoisonSerpent said:**
> Just burnt the GParted Live CD. Would it be able to make a new NTFS partition? Or can it make a partition that is readable by both Ubuntu and Windows?

Thanks,

PoisonSerpent

If it won't let you create an NTFS partition then you can use fat32 (also known as vfat) which is readable/writeable from both Windows and Linux.

---

### Post by PoisonSerpent on 2009-11-09
> **alphacrucis2 said:**
> If it won't let you create an NTFS partition then you can use fat32 (also known as vfat) which is readable/writeable from both Windows and Linux.

Sweet! Thanks to all of you.

I will reply when I recieve the laptop (within a month, or later) and tell you how it went.

---

### Post by jbrown96 on 2009-11-10
You probably don't need the separate partition for data. If it is needed in Ubuntu and XP, then it has to be NTFS or Fat32. Just make it part of your Windows partition. You can easily access all of the windows partition from ubuntu. By dividing your hard drive into more paritions, it becomes more likely that one of them will fill up, but there isn't a good way to keep certain data (like system files) accessible across partitions. Fewer, large partitions are better when possible.

Kind of violating that last rule: make /home a separate partition. This is probably one of the best things that I discovered after using linux for a while. I would resinstall (or switch distros) all the time, and I'd lose all my settings (not files because I would back them up). It's so nice if /home is separate because if you have to reinstall, you never need to worry about backing anything up. Just configure the installer to use that /home partition in the future (be sure to keep it from formatting;) ). / isn't that big. I go with 6GB, but 8GB should be conservative and safe. leave 30GB to /home. 

Unless you were planning on accessing your Ubuntu data from Windows, go with ext4. With the rigid permissions on Ubuntu, it's just not good to access Ubuntu through Windows; it's better to leave all your stuff on the NTFS drive and mount that in Ubuntu. 

Just ask and I'll clarify any of this.

I love Thinkpads. They really provide a (T61p) fantastic Linux experience. They are very solidly made. I bought mine the week after I dropped one down about 6 feet and three stairs. Not only did it survive, but the disk the CD that was being burned just kept going. Best of luck

---

### Post by tgalati4 on 2009-11-10
I bought a used thinkpad t43p.  The first thing I did was clone the drive to a 320 GB IDE Western Digital Blue drive (WD320).  It's the largest drive you can get for PATA/IDE.  About $80 US.  That takes care of the space problem.

I would make an extra ext3/4 partition for the next version of whatever linux distro that you install.  That way you always have a working linux distro.  You can expect breakage from the latest linux distro until you get everything sorted out.

I stepped on mine in the dark.  My wife had put it on the floor to move a chair.  The case can definitely handle 185 lbs!

---

### Post by sh4d0w808 on 2009-11-10
If U try to create big files - more than 2 GB - U cannot use FAT32, it is a limitation of FAT32.

---

### Post by PoisonSerpent on 2009-11-10
@sh4d0w808:

The biggest file I would probably ever use is 1.5GB (a huge .iso file). I don't know what I should do though.

@tgalati4:

I will probably get a bigger hard drive from a friend that's IDE. It's 250GB, I think that's the biggest I'll ever need. (But I remember someone saying we will never need more than 8MB storage.. hmm)

@jbrown96:

I originally wanted the seperate NTFS partition for Music storage, in case I got a virus in XP, but what I'll do is have all my music on the Ubuntu partition, then I will copy it to the Windows partition. If I get a virus, I format the partition and reinstall XP, then recopy everything from the Ubuntu partition to the XP one.

The only thing I really need XP for is iTunes. Could I run it under WINE?

---

### Post by jbrown96 on 2009-11-10
itunes will sort of run under wine, but not for anything worthwhile. You can't access the store or sync devices, so there's nothing you couldn't do with a native linux player. I use Virtualbox and run itunes inside of that with shared folders set up. I can sync stuff to my iphone, and it works reasonably well. Just DON'T TRY TO UPDATE AN IPHONE or IPOD TOUCH!!!! It will freeze when it reboots and be stuck in an infinite reboot cycle. 

Remember that Thinkpads use special hard drives. They are 1.8" instead of the normal 2.5" for laptops. IBM does this because they have shock absorbing hardware in the hard drive, so it has to be smaller. 


If itunes or other rarely used applications are all you need Windows for, I recommend try Virtualbox. It's much more convenient because you won't need to reboot.

---

### Post by sh4d0w808 on 2009-11-11
> **PoisonSerpent said:**
> @sh4d0w808:

The biggest file I would probably ever use is 1.5GB (a huge .iso file). I don't know what I should do though.

For example: if U create or download a DVD-iso file to that partition. A single layer DVD is 4.3 GB, which is over than 2 GB...

---

### Post by jbrown96 on 2009-11-11
> **sh4d0w808 said:**
> For example: if U create or download a DVD-iso file to that partition. A single layer DVD is 4.3 GB, which is over than 2 GB...

Fat32 can go up to 4GB, not 2GB. That's still smaller than a DVD iso, but for regular files it gives a lot more room.

---

### Post by sh4d0w808 on 2009-11-12
> **jbrown96 said:**
> Fat32 can go up to 4GB, not 2GB. That's still smaller than a DVD iso, but for regular files it gives a lot more room.

Ooops... really, U R right. (Why I remembered to 2 GBs?)

---

### Post by PoisonSerpent on 2010-02-08
> **jbrown96 said:**
> itunes will sort of run under wine, but not for anything worthwhile. You can't access the store or sync devices, so there's nothing you couldn't do with a native linux player. I use Virtualbox and run itunes inside of that with shared folders set up. I can sync stuff to my iphone, and it works reasonably well. Just DON'T TRY TO UPDATE AN IPHONE or IPOD TOUCH!!!! It will freeze when it reboots and be stuck in an infinite reboot cycle. 

Remember that Thinkpads use special hard drives. They are 1.8" instead of the normal 2.5" for laptops. IBM does this because they have shock absorbing hardware in the hard drive, so it has to be smaller. 


If itunes or other rarely used applications are all you need Windows for, I recommend try Virtualbox. It's much more convenient because you won't need to reboot.

Thanks.. I actually use VirtualBox on my other PCs already, to test out some Linux distros, so I am quite familiar with it.

My family got me a netbook (Gateway LT3114u) for Christmas instead, but I am still planning on using Ubuntu. The laptop has a 250GB HDD (240GB, in reality, due to a hidden partition as a factory defaults rescue system), and I will be wiping it installing Ubuntu. I will have 80GB of space for /home (I have around 20gigs of music.. and then I have all my school stuff, websites, etc.. so I probably need all of that space. =) )



I tested out UNR (Ubuntu Netbook Remix), but didn't like the way the desktop "acted" so I will be using Ubuntu 9.10.

Also, this laptop has an ATI Radeon card in it, so I will definitely be using Compiz.. muahhaha (always wanted to use Comiz, never had a graphics card to do it).


Thank you for all the advice!!

PoisonSerpent
[http://www.poisonserpent.com/](http://www.poisonserpent.com/)

---

