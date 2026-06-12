---
title: "Partitioning Vista and Ubuntu for Shared Files"
date: 2011-02-04
forum: General Help
---

### Post by _Impact_ on 2011-02-04
Hi!

I've managed to create the dual boot for Vista and Ubuntu 10.10 ([http://ubuntuforums.org/showthread.php?t=1675301&highlight=_Impact_]("http://ubuntuforums.org/showthread.php?t=1675301&highlight=_Impact_"))

The partitions look something like this (see attachment):
/dev/sda1 - Vista Recovery Environment
/dev/sda2 - Vista
/dev/sda3 - Entended partition
 /dev/sda5 - Ubuntu 
/dev/sda4 - EISA (pre-installed by manufacturer, don't really know what this is)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182708&stc=1&d=1296854870[/IMG]


Now I have about 150 GB of data on an external HD that I would like to be able to share between Windows and Ubuntu, with read and write permissions. 

I looked at this article 
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
 and am now thinking of setting up another logical partition formatted FAT32 inside the extended, after shrinking Ubuntu partition to about 20GB, then placing my data there. It would look something like that:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182709&stc=1&d=1296854870[/IMG]

Now I would like to know whether you think it's a good idea or not, and if so, what should I consider when doing that. 

Thanks!

---

### Post by Megaptera on 2011-02-04
Useful guide for that sort of scheme here [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

it's what I've done.
Vista 20 gb
Ubuntu 10gb

and 'shared data' 120gb

---

### Post by coffeecat on 2011-02-04
Having a shared data partition for both Vista and Ubuntu is a good idea, but format it NTFS, not FAT32. NTFS is more robust than FAT32, it doesn't have the 4GB filesize limit of FAT32 and NTFS read-write is reliable in Ubuntu.

FAT is still useful on flash drives but for internal partitions it needs to be consigned to the dustbin of history.

---

### Post by _Impact_ on 2011-02-04
Ok looks interesting, but what concerns me is that I already have 4 partitions on my drive, and I don't have a swap partition, so I don't know whether that tutorial will work.

I'm now thinking maybe there's a simple solution, what if I shrank the Ubuntu partition and extended the Vista partition, then saved all my files in Vista, I think I can access them from Ubuntu. 

Would that work?

---

### Post by _Impact_ on 2011-02-04
> **coffeecat said:**
> Having a shared data partition for both Vista and Ubuntu is a good idea, but format it NTFS, not FAT32. NTFS is more robust than FAT32, it doesn't have the 4GB filesize limit of FAT32 and NTFS read-write is reliable in Ubuntu.

FAT is still useful on flash drives but for internal partitions it needs to be consigned to the dustbin of history.

Thanks for the tip! Can I make this new NTFS partition for shared folders and files as a logical partition inside the extended one (due to limit of 4 primary partitions on drive)?

---

### Post by coffeecat on 2011-02-04
> **_Impact_ said:**
> 
I'm now thinking maybe there's a simple solution, what if I shrank the Ubuntu partition and extended the Vista partition, then saved all my files in Vista, I think I can access them from Ubuntu. 

Not a good idea to save files into the Vista partition on a regular basis. Sensible rule of thumb is to avoid writing to a Vista or W7 partition as much as you can - preferably never. Ubuntu NTFS write is reliable but Vista and W7 can react badly to writes from outside.

You have three primary partitions and 1 extended. If you shrink sda5, you can make as many logical partitions as you want in the extended: swap, data, whatever you want. You could also enlarge the extended partition backwards to fill the 46GB of space, but you'd have to do this from the live CD. Be aware that that could take a long time.

---

### Post by coffeecat on 2011-02-04
> **_Impact_ said:**
> Thanks for the tip! Can I make this new NTFS partition for shared folders and files as a logical partition inside the extended one (due to limit of 4 primary partitions on drive)?

Yes. Make a logical NTFS partition and Windows will pick this up automatically as D: or E: or whatever it wants to call it. Ubuntu will show it to you in Places.

Beware of looking at Linux partitions in the Windows Disk Management Utility - at least in Vista or W7. It gets confused by Linux filesystems and refers to Linux logical partitions as 'healthy' (but, of course!) primary ones. On my main multi-booting desktop, Windows 7 Disk Management tells me I have 8 primary partitions on one drive! :rolleyes:

---

### Post by _Impact_ on 2011-02-04
Thanks!!! I'm defragmenting Vista partition now to see how much space I can squeeze out and then I'll extend the !extended partition and create another logical NTFS for shared files.

---

### Post by _Impact_ on 2011-02-04
Worked like a charm!!! Thanks for your help!!!

---

