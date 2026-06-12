---
title: "Is accessing a windows partition via ubuntu on a dual boot a bad habit?"
date: 2010-08-29
forum: General Help
---

### Post by the big e on 2010-08-29
I have ubuntu and vista on a dual boot on a thinkpad t500. I have discovered that Ubuntu sees my Windows partition as if it were a separate disk drive but not vice versa. If I get into the habit of accessing the contents of my Windows partition a lot while I am on Ubuntu (for instance working on my word processing files that I originally created in Windows while on Ubuntu) is there anything I need to be careful of accidentally damaging? Is it bad for my machine to do this?

---

### Post by jerome1232 on 2010-08-29
No not really, Linux supports the nt file system very well these days.

---

### Post by howefield on 2010-08-29
> **the big e said:**
> If I get into the habit of accessing the contents of my Windows partition a lot while I am on Ubuntu (for instance working on my word processing files that I originally created in Windows while on Ubuntu) is there anything I need to be careful of accidentally damaging? Is it bad for my machine to do this?

You are not likely to do any damage to the disk nor file(s).

Although it makes sense to have all your valuable data backed up, not because of what you want to do, but because it makes sense in any event.

---

### Post by mikewhatever on 2010-08-29
It's not a bad idea, but accidentally deleting half of Windows system files with such a setup is also not unheard of.

---

### Post by jerome1232 on 2010-08-29
> **mikewhatever said:**
> It's not a bad idea, but accidentally deleting half of Windows system files with such a setup is also not unheard of.

Hehe, there's always that.

---

### Post by ajgreeny on 2010-08-29
A better way to do this is probably to make a new /data partition formatted to ntfs and make that mount at boot time.  You will still be able to access files, and with the correct /etc/fstb file entry, edit the files in ubuntu, but it will keep ubuntu away from the windows OS system files.

---

### Post by srs5694 on 2010-08-29
> **ajgreeny said:**
> A better way to do this is probably to make a new /data partition formatted to ntfs and make that mount at boot time.  You will still be able to access files, and with the correct /etc/fstb file entry, edit the files in ubuntu, but it will keep ubuntu away from the windows OS system files.

+1.

I disagree with most of the posters before ajgreeny; IMO accessing *any* OS's main boot partition from another OS on a regular basis is asking for trouble. Although the NTFS-3g drivers that Linux uses for accessing NTFS are pretty reliable, they're still reverse-engineered and could conceivably trash the filesystem. More important, Linux doesn't understand the NTFS file ownership and security systems, meaning that it's far too easy for an ordinary user to completely trash files that Windows would never allow an ordinary user to damage if Windows were booted. (This is mikewhatever's point, but I disagree with his initial "it's not a bad idea" statement -- IMO, the fact that it's so easy to do such damage makes it a bad idea to risk it!)

I realize that most Windows installations don't separate system from user data, making this sort of access convenient and even necessary if you just shrink the Windows partition. In the long term, though, creating a separate shared-data or user-data partition for use by both OSes is safer.

---

### Post by the big e on 2010-08-29
Thank you everybody, especially ajgreeny and srs5694 for the third-partition idea. Now, how do I go about creating a third partition? Do I have to shrink the VIsta partition yet again to do that? And then what do I use to create the new partition? Should I do that within Windows or within Ubuntu?

---

### Post by Alver on 2010-08-29
I run a dual boot W7 64 / U 10.04.1 64. My original set-up was only W7 on C: and all data on D: (2 partitions on one hd). To install U 10.04.1 I shrunk my D: and used the unallocated space to install Ubuntu. This allowed me to continue to use D: for new data and access of older data files. I do not play around in the original C: where W7 is installed, ever.
Hope this helps.

Alver

---

### Post by mikewhatever on 2010-08-29
> **the big e said:**
> Thank you everybody, especially ajgreeny and srs5694 for the third-partition idea. Now, how do I go about creating a third partition? Do I have to shrink the VIsta partition yet again to do that? And then what do I use to create the new partition? Should I do that within Windows or within Ubuntu?

Unless there is another partition you can shrink, yes, you'd have to shrink the Vista partition. To format the unallocated space, use either Vista's tools or Gparted from Ubuntu.

---

### Post by Alver on 2010-08-29
> **mikewhatever said:**
> Unless there is another partition you can shrink, yes, you'd have to shrink the Vista partition. To format the unallocated space, use either Vista's tools or Gparted from Ubuntu.
I shrunk my original D: partition from within Windows 7 using Partition Wizard Home Edidtion 5.0 (freeware) and then, using the live dvd gave the install instructions to use the largest available free space (this is the unallocated space!). You DO NOT have to format anything, everything is carried out flawlessly by the Ubuntu installer. Some 40 minutes later I had 10.04 up and running.

Alver

---

### Post by the big e on 2010-08-29
If I create a new partition from within Ubuntu, will Windows not see it, just the way it doesn't see Windows' own partition?

---

### Post by howefield on 2010-08-29
> **the big e said:**
> If I create a new partition from within Ubuntu, will Windows not see it, just the way it doesn't see Windows' own partition?

As long as you format the new partition as ntfs, Windows will see it.

---

### Post by Nybb on 2010-08-29
I've been looking around for a way to make it so that I can access my music library from both my Ubuntu and Windows 7 partitions, and stumbled upon this thread. I was a little leery of just directly accessing the Windows side from Ubuntu, but this seems like a perfect solution. So, I can just boot using the Ubuntu Live CD, fire up GParted, make a new partition formatted as NTFS, and everything will work out?

---

### Post by Ravensound on 2010-08-29
I run dual boot vista/8.10 acer laptop also xp/8.10 on an old desktop, the latter with revised partitions via ubuntu setup.  I regularly copy non-sys files across both from ubuntu and have never had any problems. You might get an admin error from windows after a ubuntu re-partition but it will usually clear on re-boot.

---

### Post by howefield on 2010-08-29
> **Nybb said:**
> I can just boot using the Ubuntu Live CD, fire up GParted, make a new partition formatted as NTFS, and everything will work out?

Pretty much, yes.

Although if you are taking space from the Windows 7 partitions, I'd defragment Windows first, and preferably use a Windows application. 

(GParted should manage it fine, I just like using windows applications on windows file systems and linux applications on linux file systems).

---

### Post by Nybb on 2010-08-29
> **howefield said:**
> Pretty much, yes.

Although if you are taking space from the Windows 7 partitions, I'd defragment Windows first, and preferably use a Windows application. 

(GParted should manage it fine, I just like using windows applications on windows file systems and linux applications on linux file systems).

Alright, thanks for the tip!

---

### Post by mikewhatever on 2010-08-29
> **Alver said:**
> I shrunk my original D: partition from within Windows 7 using Partition Wizard Home Edidtion 5.0 (freeware) and then, using the live dvd gave the install instructions to use the largest available free space (this is the unallocated space!). You DO NOT have to format anything, everything is carried out flawlessly by the Ubuntu installer. Some 40 minutes later I had 10.04 up and running.

Alver

That's in case one wants to install Ubuntu. The OP doesn't want that as Ubuntu is already installed.

---

### Post by HeadHunter00 on 2010-08-29
Not unless you are drunk, or are a drugee.

---

### Post by HeadHunter00 on 2010-08-29
> **howefield said:**
> Pretty much, yes.

Although if you are taking space from the Windows 7 partitions, I'd defragment Windows first, and preferably use a Windows application. 

(GParted should manage it fine, I just like using windows applications on windows file systems and linux applications on linux file systems).
good man. yep, that is another good way to make sure that you dont break your windows partition. you never know what ballmer puts into those machines. :lolflag:

---

### Post by Mark Phelps on 2010-08-30
To respond to your original question ... YES ... it IS a bad idea ... IF the partition is a Vista/Win7 OS partition.

Those seem especially prone to improper shutdown problems and should that happen, you'll have a very hard time getting back into Vista/Win7 to run CHKDSK to fix them.

Data partitions don't present the same problems because you're not booting using them.  So, sharing data partitions is not running any real risks.

---

### Post by julio_cortez on 2010-08-30
> **ajgreeny said:**
> A better way to do this is probably to make a new /data partition formatted to ntfs and make that mount at boot time.  You will still be able to access files, and with the correct /etc/fstab file entry, edit the files in ubuntu, but it will keep ubuntu away from the windows OS system files.
This, and..
> **Mark Phelps said:**
> Data partitions don't present the same  problems because you're not booting using them.  So, sharing data  partitions is not running any real risks.
This.
I'd never automount or access a Windows partition in Ubuntu (unless it's strictly necessary e.g. disaster recovery).

In my opinion the best way to behave is to leave the Windows partition alone (and unmounted), and use another ntfs partition for data exchange (I have one automounted by default in **/media/Data** and it works flawlessly).
Of course you'll have to edit the ***/etc/fstab*** file to get it automounted at startup, but it's really simple..

---

### Post by the big e on 2010-08-31
So, if I set up a third partition, can I also put a music library on it and have it available to both identities of my machine? I guess that's a Windows question about whether Media Player or Itunes finds it acceptable for the library to live at a nonstandard location.

---

### Post by jmore9 on 2010-08-31
I switched over my internet machine to Ubuntu 10.04 and being the lazy person i am i did not bother changing the storage drive.  It is still formated in NTFS and i have not had any problems with it what so ever.

I have it mounted at boot and use it just like any storage partition.

And as for as shrinking and partitioning goes  i always us GParted Live cd.  It makes everything a lot easier.

---

### Post by DogMatix on 2010-08-31
On my desktop I whacked in another HDD. I then saved my music library, photos and other personal stuff onto this so it could be accessed by my dual boot Ubuntu/Windows setup which is on the original HDD. This also protects my personal data from OS **** ups or disk failure. I also share the new drive on my home network so I can access the music, etc from my laptop.

---

### Post by the big e on 2010-09-04
So what is a good size for the new partition. How big does it need to be if I want a music library on it? How much is it safe to shrink Vista's partition to?

---

### Post by oldfred on 2010-09-04
Windows (and most systems) need extra space. The NTFS system seems to need extra like about 30% free or it starts to slow down.

Do not know how much data/music you have, but it pays to be generous if you have space.

---

### Post by the big e on 2010-09-14
So I tried to do it, and I couldn't. Why? There are too many partitions already!

One for Ubuntu (which is anonymous on the map that Windows shows me), another anonymous one of about 1.3 gb (for Grub or a Windows bootloader?) and two partitions called Lenovo and Service that contain restore utilities and the like. So even though I was able to free up some shrink space I was not able to create another partition. When I tried to run the wizard, it took me through all the steps and then it gave me a "too many partitions" error. Any suggestions?

(This is a Lenovo ThinkPad.)

---

### Post by oldfred on 2010-09-14
You do not need a /boot, just / (root) & swap. You can put both into one extended partition and make each a logical partition inside the extended partition. Linux boots fine from logicals, windows does not.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

Expanding/Resize an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by joho68 on 2010-09-15
If proper care is taken, I can't see any problems with mounting any type of NTFS partition from Linux, regardless of the operating system that resides on the NTFS partition(s). I've been dual booting for as long as I can remember and have never had any issues with it.

Like someone pointed out, if you start removing stuff left-right-&-center from the NTFS partition, you may get into trouble. OTOH, you "may" experience the same thing if you sudo or root into a Linux environment and remove all of /bin, /lib, or /boot or some other mission critical stuff :-)

For the sharing of the obvious (multimedia files), a simple NAS is of course another alternative, that may make sense -- or an external USB disk for which just about any OS in use has support for :-) But one could also opt to only mount the NTFS partitions in read-only mode, which should prevent any form of abuse. It may, however, limit what you can from the Linux end of things.


-joho

---

### Post by srs5694 on 2010-09-15
> **joho68 said:**
> If proper care is taken, I can't see any problems with mounting any type of NTFS partition from Linux, regardless of the operating system that resides on the NTFS partition(s). I've been dual booting for as long as I can remember and have never had any issues with it.

Like someone pointed out, if you start removing stuff left-right-&-center from the NTFS partition, you may get into trouble. OTOH, you "may" experience the same thing if you sudo or root into a Linux environment and remove all of /bin, /lib, or /boot or some other mission critical stuff :-)

Your example proves the point that I and others have made in this thread. Specifically, to do serious damage to a Linux installation, you've got to go to the effort of using sudo or logging in as root. If you set up a system to mount the Windows boot partition so that it's easy to use as an ordinary user, though, you *don't* need to use sudo or log in as root to completely trash the Windows installation from within Linux. Since most things most people do in Linux on a day-to-day basis do not need root access, the risk of damage to Linux is low, but is much higher to Windows if it's mounted for easy user access.

I grant that many people use such setups without destroying their systems. It's also true that many people drive all their lives without using seatbelts and don't get killed because of it. That doesn't prove that seat belts are useless, though; *if* you're in an accident, seat belts can save your life. Likewise, *if* you mistype a command or accidentally drag-and-drop the wrong files in a GUI file manager, your Windows installation will be safer if it's not mounted. Given enough people, *if* becomes *when,* even if "proper care" is taken.

---

### Post by joho68 on 2010-09-16
I absolutely agree -- which is why I also mentioned the possibility of a read-only mount. If all you want to do is to "listen to music" or "view multimedia" that is located in the NTFS sphere, you're good-to-go. One thing that can (finally) be said about Linux support for NTFS is that it work -- which is a huge step in a good direction.

The need is very real if you have to use Windoze for one reason or another, and not everyone can afford (or want) a 2TB NAS to store their precious music on :-) In the end, this comes down to the user I guess.

You can drive a car without wearing a seatbelt, and you can place a server on the Internet without a firewall, and you may even get away with it -- but that doesn't mean it's necessarily a good idea.

:popcorn:


-joho

---

