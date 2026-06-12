---
title: "&quot;Very slow copy/rsync speeds ext4 to NTFS&quot;"
date: 2011-06-15
forum: General Help
---

### Post by Utrader on 2011-06-15
Hi,

I started to asked questions about this in another thread 
("**Re: NTFS-Config Side Effect: All Files Are Executable**") so that is why I started this new thread about this question:
 
What I'm trying to achieve is to use luckybackup to sync two hdd drives (one ntfs and one etx4) connected via USB. The transfer speed to the NTFS hdd is very low (29kb/s) but if I open a terminal (works every time) and write 'sudo ntfs-config' the speed goes up to 30Mb/sec.

---

### Post by Utrader on 2011-06-15
Coffecat have tried to help me out and wrote that should test copying ext4 > NTFS:
I did that with same result (about 29KB/sec)
 
Coffecats answer:
That is very significant. You ought to be getting a speed of somewhere between about 10-40 MB/Sec depending on hardware factors. Even with an old 2½" laptop drive in an USB enclosure and hence slow, copying ext4 > NTFS I am getting a steady 10.5 - 11.0 MB/Sec. I don't know whether Morbius1 has a view on those NTFS mount options, but getting proper transfer speeds by invoking ntfs-config is a bit like getting a faulty freezer to work by opening the back door in winter. It's the wrong approach.

I'm sorry, but I don't have any ideas at the moment as to why your transfer speeds are wrong.

---

### Post by Utrader on 2011-06-15
I then have changed direction (after understanding that this was not an easy task to solve):

I will try the other way around :smile:

I'm going to try the program "Ext2Read" ([[COLOR=#444444]http://sourceforge.net/projects/ext2read/[/COLOR]]("http://sourceforge.net/projects/ext2read/")) for Windows. With that program I should be able to read from an ext4 hdd from Windows. If that seems to work the way I hope I will then format my ntfs hdd to ext4. 

After that I'm sure all the backup programs I have tried for Ubuntu will work the way I expect.

---

### Post by Utrader on 2011-06-15
Next information Coffecat gave me was:
"If you format the drive ext4, you will immediately have permissions problems in Ubuntu unless you set appropriate mount options in /etc/fstab or do some chmod and chown commands on the ext4 filesystem. Personally, I prefer the latter, but there are plenty of people to help with either way."
=================
My answer to that was:
So, next question:
How do I do some chmod and chown commands on the ext4 filesystem?

I have not done so for the ext4 hdd that I have so that might be a reason for low transfer speed or?
=================
Coffecat answered:
I thought you were only getting low transfer speeds to NTFS. If you are getting low transfer speeds to ext4 then something is seriously wrong somewhere and no amount of chmodding and chowning is going to help.

This is getting unfair on the OP. Thread hijacks are frowned on in this forum. If you start your own thread and pm me with the link, I'll mosey over and help you with the chmod and chown bit, but I can't say that I can help with low transfer speeds.
=================
...to be continued (I hope)

---

### Post by coffeecat on 2011-06-15
I've asked a couple of other people to have a look as well. Hang in there! :)

---

### Post by Utrader on 2011-06-15
You're the one!

---

### Post by coffeecat on 2011-06-15
@Utrader, there's an art to starting a thread in such a way that it encourages people to stop by and make suggestions. Unfortunately, you did not provide a link to the previous thread and I think you've left out some important information. Let me see if I can help you. :)

 The previous thread was here:

 [http://ubuntuforums.org/showthread.php?t=1775844](http://ubuntuforums.org/showthread.php?t=1775844)

 My understanding of what you told us is that at some time you installed ntfs-config and ran it, after which your /etc/fstab looks like this:

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be5790c8-d0fb-46d8-93c0-f351be696a0b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb5 :
UUID=1716A2A8B49B49B1    /media/FILMER-1Tb    ntfs-3g    defaults,nosuid,nodev,locale=sv_SE.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=02547D39547D3091    /media/sda1    ntfs-3g    defaults,locale=sv_SE.UTF-8    00
#Entry for /dev/sda6 :
UUID=37781d32-9066-4110-ac54-1d76f6d843c4    none    swap    sw    0    0
``` When you were running luckybackup (which I believe is a front-end to rsync) you found that the transfer speed to a USB drive formatted NTFS was only 29KB/s, but that when you ran “sudo ntfs-config” from a terminal, the speed jumped to 30MB/s. You found the same when using other front-end apps to rsync and when you tried an ordinary drag and drop copy of files from an internal ext4 partition to the NTFS drive, speed was also very slow, thus suggesting the problem is not specifically with rsync.

 You were asking whether it was possible to get ntsf-config to run on bootup. I pointed out that yours was a very unusual observation, that the speedup was probably due to an unexpected consequence of running ntfs-config and that it would be better to investigate why the transfer speed is so slow.

 At one point you seemed to suggest that transfer speed to an ext4 partition was also slow, but I may have misunderstood you. Perhaps you could confirm this one way or the other.

 Please correct me if I have any of the above wrong. It seems to me that we need to investigate what is causing the slow transfer speed to ntfs, because most people do not experience this. I certainly do not. Or, if transfer speed to ext4 is OK, then we can investigate the possibility of using ext4 in your external drive(s) and I was going to help you with the permissions and ownership issues involved with that.

 Is that a fair summary?

---

### Post by Utrader on 2011-06-15
Coffecat:
Many thanks for the good summary :)
 
> **coffeecat said:**
> At one point you seemed to suggest that transfer speed to an ext4 partition was also slow, but I may have misunderstood you. Perhaps you could confirm this one way or the other.
 
You must have missunderstod me , I have not experinced any problem when using ext4 hdd as the destination.
 
From the beginning both hdd were ntfs but when I found the infomation about the problem writing to ntfs hdd and the "ntfs-config" info I formated one hdd to ext4 and that hdd has always had a transfer speed to 30Mb/s when used as the destination (in other words, I have not found any problems to use the ntfs hdd as a source).
 
I have not done any permission corrections for any of the hdd like appropriate mount options in /etc/fstab or some chmod and chown commands on the ext4 filesystem.

---

