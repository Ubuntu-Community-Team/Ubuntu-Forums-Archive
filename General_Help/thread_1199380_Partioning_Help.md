---
title: "Partioning Help"
date: 2009-06-28
forum: General Help
---

### Post by samuel.faith on 2009-06-28
Hi guys,

Just last day I reinstalled Jaunty as fresh install due to some reasons. However I left my /home partition as it is as I don want to touch my files. During the installation, I resized one of my NTFS partition (it got 30GB free space) to get extra 10GB free space for my Ubuntu. My intention was to format that free space to ext3 and install EVE on it.

But after resizing is done, I couldn't get the installer to create a new partition on that unallocated space. So I left it as it is and proceeded with the installation, thinking I will use GParted later to do the job.

But alas, as I already have 4 primary partitions (one is Extended Partition) I cannot create another partition again! And I also don't know how to copy move that unallocated space under Extended Partition either.

I have attached the screenshot and I am sure somebody out here can help me. Right now I am stranded with 10GB of space unallocated and unusable :D :D.

Thanks in advance!

Regards,

Samuel Faith

---

### Post by egalvan on 2009-06-28
You can move /sda3 to the left, then expand /sda4.

But I don't remember if you can change an extended partition if it currently has logical partitions...


BTW, depending on how much RAM you have, and what you use your machine for, 2.86GB for swap is excessive.

I have machines with 2GB up to 8GB, and have settled on 1GB for swap.
I watch TV, DVD, Firefox, etc and have never used more than 24Meg of swap.

Hibernation uses a swap size equal to RAM, so this is a concern if you hibernate your laptop... I never do.

One more thing to consider....

---

### Post by samuel.faith on 2009-06-28
> **egalvan said:**
> You can move /sda3 to the left, then expand /sda4.

But I don't remember if you can change an extended partition if it currently has logical partitions...


BTW, depending on how much RAM you have, and what you use your machine for, 2.86GB for swap is excessive.

I have machines with 2GB up to 8GB, and have settled on 1GB for swap.
I watch TV, DVD, Firefox, etc and have never used more than 24Meg of swap.

Hibernation uses a swap size equal to RAM, so this is a concern if you hibernate your laptop... I never do.

One more thing to consider....


Hi egalvan,

Thank you for your information. Currently I have 3GB RAM. Exactly I set swap space almost same as RAM due to hibernation reason. :) As I am on a lappy, I usually put my lappy into hibernation mode if I am on move.

And would you mind to provide additional details about expanding /sda4? I understand how to move /sda3 to the left (again here, will it harm the data on it?), but I don't quite get about how to expand /sda4.

Thank you so much!

Regards,

Samuel

---

### Post by egalvan on 2009-06-29
> **samuel.faith said:**
> Hi egalvan,

I have 3GB RAM... I set swap space almost same as RAM due to hibernation
  As I am on a lappy, I usually put my lappy into hibernation mode if I am on move.

As I stated, I don't use hibernate anymore, never found it to be faster than shutdown/starhttp://partedmagic.com/tup.
And hibernate under Linux was problematic in the past.

> And would you mind to provide additional details about expanding /sda4?
 I understand how to move /sda3 to the left (again here, will it harm the data on it?), but I don't quite get about how to expand /sda4.


gparted won't perform some operations on extended partitions if they are not empty...
this may or may not be valid for re-sizing a partition...

My test machine is down for up-grades, so I can't play with this now to confirm...

Anyway, after moving the /sda3 partition, you can try re-sizing the extended partition /sda4.
select it, and then drag the left side to the left...
taking up the empty space that remains after the move...
or use the size roller to increase the size...

Two things....

I STRONGLY suggest making copies of any data you don't want to lose...
mucking around with partitions is a good way to lose data...
BACK IT UP!

Second, I recommend using PartedMagic LiveCD to do the work...

[http://partedmagic.com/](http://partedmagic.com/)

it's a full distro designed to facilitate partitioning jobs...
very well made, it strives to have the latest gparted, which the UbuntuLiveCD may not...
It will also clone partitions and drives, and has full file system support, and network.
You can play Solitaire or surf the Internet while doing partition work ;)

If you use it and find it useful, please consider donating a buck or two to the authors...

I've used it for almost two years, and donate $5 a year...it's worth it...
(I'm using it in my business (computer repair), so I'll be starting a monthly sponsorship)

---

### Post by samuel.faith on 2009-06-29
Ah! Thank you so much egalvan. You really save my day! I will heed your advice and use PartedMagic LiveCD for the job.

What software in Linux do you usually use for backup? Right now I am using DropBox for backing up my essential work files and my assignment papers. As I am using their free version, my storage is only about 2GB.

I have a few external hard drives and usually I just copy my important folders onto them, updating regularly for once a week.

However, what I am looking for is to backup/clone at least Linux installation, or perhaps entire drive, onto external hard-drive. Probably on schedule or when I want to back it up. As I am not so familiar with backup systems, closest example I can give is Snapshot feature from VirtualBox. We can just take a snapshot of the guest OS installations and if we want to roll back, we can use those snapshots. I think TimeMachine from Apple is something like that? Yeah, that&#347; what I am really looking for.

All the best with your business, buddy :). Thank you so much for your help!

Regards,

Samuel

---

