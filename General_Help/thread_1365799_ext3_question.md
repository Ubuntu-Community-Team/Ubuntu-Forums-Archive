---
title: "ext3 question"
date: 2009-12-27
forum: General Help
---

### Post by mod-jkl on 2009-12-27
Hi,

I installed ubuntu 9.04 with the ext3 filesystem. I used before reiserfs because this filesystem never asked questions to the user when doing a fsck or after a power outage (what to do with this inode etc ...) and this is what I'm looking for for this pc. 
That was not the case a few years ago with mandriva and ext3 where the user was asked technical questions after a power outage for instance.

The question is, how is it today with ubuntu jaunty/ext3 ?

Thanks for any information

---

### Post by warfacegod on 2009-12-27
I used ext3 for about 1.5 years and never had any issues with power losses. I switched to ext4 .5 years ago and it's the same, zero problems Neither one has asked me any "technical questions" either. I'm also very pleased with their performance, it's much better than say FAT32 or NTFS.

---

### Post by mod-jkl on 2009-12-27
Thanks for the information. One last question, does ubuntu performs an fsck every 6 months or so on ext3 filesystems ? that was the case before with Mandriva/ext3.

---

### Post by dcstar on 2009-12-27
> **mod-jkl said:**
> Hi,

I installed ubuntu 9.04 with the ext3 filesystem. I used before reiserfs because this filesystem never asked questions to the user when doing a fsck or after a power outage (what to do with this inode etc ...) and this is what I'm looking for for this pc. 
That was not the case a few years ago with mandriva and ext3 where the user was asked technical questions after a power outage for instance.

The question is, how is it today with ubuntu jaunty/ext3 ?

Thanks for any information

Every Ubuntu user has (always) been able to have any filesystem errors fixed automatically be changing one file: /etc/default/rcS

```
FSCKFIX=yes
```

Set this and you will not be prompted, everything will be automatically answered "Yes".

---

### Post by mod-jkl on 2009-12-27
That's great, thanks a lot for your help.

---

### Post by Zoot7 on 2009-12-27
Ext3 has been around for a very long time now. It's pretty tried, tested, stable and relatively problem free by now.

I've been migrating the huge plethora of stuff i've stored on NTFS hard drives to Ext3 filesystems instead due to the fact I've had a few ntfs systems go down the toilet. 
But to answer your query, pretty darn stable. :)
[QUOTE=mod-jkl]One last question, does ubuntu performs an fsck every 6 months or so on ext3 filesystems ? that was the case before with Mandriva/ext3.[/QUOTE]
It does it by number of mount and every 180 days (I think), you can tweak the number of mounts using the **tune2fs** tool.

---

### Post by warfacegod on 2009-12-28
It's something like every 50 boots, if my memory serves.

---

### Post by falconindy on 2009-12-28
Default is 25. Ext3 is rock solid and will not let you down. If you wanna live on the edge, use btrfs.

---

### Post by zey on 2009-12-28
ext3 is very stable file system, never crash before.
You will have no worry to use this type of file system.

ext4 is not stable yet, sometimes has problem with big size file operation.
But, I'm using Karmic and use ext4... so far so good




[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by mod-jkl on 2009-12-28
Thanks your answers, I did put FSCKFIX=yes in /etc/default/rcS and set the file system to do a check every 100 mounts:
 
sudo tune2fs -c 100 /dev/sda1 

Just one last thing, is the 100 mounts value safe, can I use a bigger value .. ?

This pc is used a small amount of time avery day to do mail, a little web brosing, etc ...

---

### Post by colintivy on 2009-12-28
> **zey said:**
> ext3 is very stable file system, never crash before.
You will have no worry to use this type of file system.

ext4 is not stable yet, sometimes has problem with big size file operation.
But, I'm using Karmic and use ext4... so far so good




[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

Hi folks,

This thread is very informative,advice not found elsewhere that I have looked at. I am planning to anticipate the next LTS by getting my /home on its own partition. Needing to back it up, I wish to use an external USB HD.that is spare. Presumably this will have to be reformatted, after its use with a Win98 system, and ext3 or ext4 filesystem used. Will this have to be specified in advance? Will 10.04 need Ext4 or is it likely not to be fussy?

colintivy :confused:

---

