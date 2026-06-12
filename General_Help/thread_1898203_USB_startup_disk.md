---
title: "USB startup disk"
date: 2011-12-20
forum: General Help
---

### Post by maghoxfr on 2011-12-20
Hello,

I am formatting my pc right now. I will reinstall both OS's from the scratch but I have no CD-DVD burner and nor do I have a pendrive.

My options are the very same external HDD I have backed everything in or my philips go gear vibe 8GB mp4 player.

My question is:
Can I use any of those devices as a startup disk WITHOUT losing the information I have in them?

(I don't care about the music on the mp4 player but I wouldn't want to screw it up by deleting its "OS" or whatever t's called)

Thank you

---

### Post by maghoxfr on 2011-12-26
Anybody? I still have this doubt. Thanks.

---

### Post by snowpine on 2011-12-26
You should be able to buy a 1gb or larger flash drive for under US$5 with all the after-holiday sales that are going on.

---

### Post by maghoxfr on 2011-12-26
I don't have a CD burner and I don't have $5 to spare at this time. But thanks, I'll find a way.

---

### Post by West201 on 2011-12-26
I believe you can't boot from an external drive without formatting the device. Are still able to boot to Windows or Ubuntu ? 

If so you can use gparted or other partitioning application to create a partition for Windows. Format the partition in NTFS, you can then install Windows in that partition, and then transfers your files there. It's easier to install Ubuntu after Windows is already installed, Since the Windows will not recognize the Ubuntu partition at first.

---

### Post by maghoxfr on 2011-12-26
> **jessejj89 said:**
> I believe you can't boot from an external drive without formatting the device. Are still able to boot to Windows or Ubuntu ? 

If so you can use gparted or other partitioning application to create a partition for Windows. Format the partition in NTFS, you can then install Windows in that partition, and then transfers your files there. It's easier to install Ubuntu after Windows is already installed, Since the Windows will not recognize the Ubuntu partition at first.

That's a great solution! I will deffinitely try it. Thank you very much.

---

### Post by West201 on 2011-12-26
> **maghoxfr said:**
> That's a great solution! I will deffinitely try it. Thank you very much.

After you install Windows, you'll have to use an Ubuntu live cd to access your files in your Ubuntu partition, you can then transfer them to Windows. Or follow the method below.

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by maghoxfr on 2011-12-26
> **jessejj89 said:**
> After you install Windows, you'll have to use an Ubuntu live cd to access your files in your Ubuntu partition, you can then transfer them to Windows. Or follow the method below.

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

Thanks mate!

---

