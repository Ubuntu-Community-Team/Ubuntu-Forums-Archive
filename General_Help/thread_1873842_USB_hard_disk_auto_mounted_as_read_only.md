---
title: "USB hard disk auto mounted as read only"
date: 2011-11-02
forum: General Help
---

### Post by Anayonkar.Shivalkar on 2011-11-02
[SIZE=2][FONT=&quot]Hi,[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]This is my first post in Ubuntu Forum.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]I’m using Ubuntu 11.10 64 bit since last 2 weeks and I’m absolutely enjoying it.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]However, since today morning, I’m facing an issue regarding USB HD.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]Till yesterday, I did not face any such issue but now USB is getting auto-mounted as read only.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]I suspect this is something to do with upgrade I made yesterday (perhaps some USB driver got installed or upgraded).[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]Also, I searched for such issues and found that this might be an issue due to corrupt file system of USB.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]I’m having NTFS on USB and it is still working fine on Windows 7 so I guess file system is fine.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]Please let me know what can be done in such case. Will ntfs-3g be helpful? I want USB to be auto-mounted as read-write.[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]Thanks.[/FONT][/SIZE]

---

### Post by Bradburts on 2011-11-02
Identify your hard drive in ```
/etc/fstab
```
You may have a line like:
```
 
 /dev/mapper/usb-drive/               ext4    noatime,**errors=remount-ro** 0       1


```
 
So if there is an error then your drive will be remounted read only.
Don't just remove the remount option as you need to fix the error before it gets serious!
I would run a disk check on your drive first, hopefully that will pick up an error and fix it.

---

### Post by Anayonkar.Shivalkar on 2011-11-02
Thanks Bradburts.

However, is it possible to scan/repair ntfs file system using fsck? How?

Also, if file system had problems, it would've shown errors on windows too. But I'm able to write on USB on windows.

Anyways, I'll backup all data and scan file system.

Please advice how it can be done.

How about using
```

fsck -F ufs -y /dev/sdb1

```or using fsck.ntfs (or fsck.ntfs-3g or ntfsfix, or should I simply run chkdsk from windows)?

Please suggest.

Thanks.

---

### Post by Anayonkar.Shivalkar on 2011-11-02
Hi,

Instead of going for fsck on USB, I booted my laptop with Ubuntu 11.10 live DVD and checked if I'm able to write on USB.
Surprisingly, I can write data on it, thus now it seems that problem is with my root partition.
So, I did fsck on it, and found some errors (invalid length 0 for inode - or something like that). Since I used -p option, those errors were expected to be repaired.
Obviously, next time when I did fsck on root partition, there were no errors.

Now, when I boot into my  system, *still* same issue occurs. I'm not able to write anything on USB. Also, since I'm able to do so via live DVD, I'm pretty sure that there's no issue with USB and I don't have any intention to spend time in 'fsck'ing 1TB USB.

Can anything be done here (apart from reinstalling OS)? If reinstalling is the only option, and this is my 3rd week with Ubuntu, I would really think about installing Ubuntu again :(

Suggestions welcome.

Thanks.

Edit:

Line from /etc/fstab:
UUID=22812dbb-ff28-40d1-ac0c-fd9979bb57bc /               ext4    errors=remount-ro 0       1

Line from mount command:
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)

Is this (errors=remount-ro) expected?

---

### Post by coffeecat on 2011-11-02
@Anayonkar.Shivalkar, NTFS-formatted external drives should be automounted read-write out of the box. However...

> **Anayonkar.Shivalkar said:**
> I suspect this is something to do with upgrade I made yesterday

This is possible. Some people are reporting that the ntfs-3g package in 11.10 (which you mention in your first post) is possibly being removed during an update or upgrade. I've done two upgrades from 11.04 and kept two other 11.10 systems up-to-date and I've not seen this, nevertheless other people are. Some are accidentally allowing the package-manager to remove ntfs-3g by installing ntfsprogs which is not needed in 11.10 and conflicts with ntfs-3g.

Whatever the underlying cause for a missing ntfs-3g might be, check that you do have ntfs-3g installed. If you don't, install it. It will remove ntfsprogs if you have installed that, but that doesn't matter because the version of ntfs-3g that comes with 11.10 includes the utilities previously supplied by ntfsprogs.

---

### Post by Anayonkar.Shivalkar on 2011-11-02
Hi coffeecat,

I was just going through libraries which were updated recently and figured out that ntfsprogs was recently installed (yesterday).

Also, I was thinking to install ntfs-3g, but apt-get gave me a warning that it would remove ntfsprogs and I was wondering what should I do.

Your post came just in time! Thanks a ton!

I went ahead with ntfs-3g and guess what, I'm now able to write on my HD (I haven't even rebooted machine, simply plugged out USB and plugged in again).

Thanks a lot everybody. It feels good when your issue gets resolved in just around 12 hours :P

---

### Post by coffeecat on 2011-11-02
> **Anayonkar.Shivalkar said:**
> 
I went ahead with ntfs-3g and guess what, I'm now able to write on my HD (I haven't even rebooted machine, simply plugged out USB and plugged in again).


I'm glad it worked. Please pass the word around about ntfs-3g and ntfsprogs if you can. I'm not saying that people are mistaken in saying that upgrades have removed ntfs-3g - I really don't know - but I'm sure some of the reports about ntfs-3g going missing is due to the installation of ntfsprogs.

Good luck! :)

---

### Post by raghu.k on 2012-03-18
Thank you guys this post really helpful.
I installed ntfs-3g [removed ntfsprogs] and it worked like a charm.
It's a relief.

---

