---
title: "Hard Drive Switch Ghost"
date: 2006-06-27
forum: General Help
---

### Post by brownrl on 2006-06-27
Been searching around and I haven't found one that covers exactly what I am looking for.

Getting a new hard drive... bigger cheaper faster yada yada yada

I want to completely move everything ( OS, grub, passwords, accounts, cookies, you name it ) to the new hard drive and boot from that one.

Then take the old on out and put it into another machine.

I got my ubuntu just the way I like it and I don't want to re-install for this machine. Like ghost the old one to the new one.

Whats the best way to do this?

Thanks in advance
Rob

---

### Post by glinsvad on 2006-06-27
[http://www.ubuntuforums.org/showthread.php?t=35087]("http://www.ubuntuforums.org/showthread.php?t=35087")

---

### Post by newman on 2006-06-27
I used partimage to image my harddisk and it was quite easy.  I used Ghost many times in the past with windows, but I read that even though  Ghost ver. 7.5 + is supposed to support ext3 file system it can hose your system, so I didn't take the chance.  I just started the computer with a boot cd (systemrescuecd) and used partimage to image the entire drive (hda1) to second drive (hdc1).  Do a search for partimage and you will find what you're after...

---

### Post by glinsvad on 2006-06-27
[QUOTE=newman]I used partimage to image my harddisk and it was quite easy.  I used Ghost many times in the past with windows, but I read that even though  Ghost ver. 7.5 + is supposed to support ext3 file system it can hose your system, so I didn't take the chance.  I just started the computer with a boot cd (systemrescuecd) and used partimage to image the entire drive (hda1) to second drive (hdc1).  Do a search for partimage and you will find what you're after...[/QUOTE]

The reason I suggested backup/restore by zipping files is to make the harddrive switch easy. If you make an image of one harddrive and then just expect it to "fit over" the new one, you might be in for a surprise. Besides tarballing is a lot more flexible in my opinion, cause you don't waste time and space backing up useless files or even empty space...

---

### Post by brownrl on 2006-06-28
Thanks for the help.

So here is what I am thinking let me know if you can or if this right?

1. put the new hd in and install base / rescue ubuntu on it as master boot drive
2. then take new hd out and put it on secondary ide channel
3. put old one back in and boot like normal
4. copy everything from old to new except for dev proc mnt and a few others
5. take old hd out and switch new hd to master boot ide channel again

Then it should be exactly the same? Theme, passwords, software, files...?

I always thought that somethings like the /etc/password file was very system/hd specific. 

Thanks again
Rob

---

### Post by aysiu on 2006-06-28
I disagree with glinsvad. PartImage makes a backup of the image of what's *used* on your partition, not the entire partition or drive, so it's easily transferrable to another drive.

Instructions for it are here:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by brownrl on 2006-06-28
Ok I think I got it:

1. put new hd in
2. boot with live cd
3. install partimage
4. partition new hd like the old one
5. partimage from old to new
6. switch old for new
7. boot live cd again and install grub on new hd
8. reboot and it should be like nothing happened except that I should have more space on the hd ( newer bigger hd )?

does that seem reasonable?

Thanks again.
Rob

---

### Post by newman on 2006-06-28
You don't need to install partimage - it runs off a live cd. Download >>
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")
and run the live cd. From there you can run QtParted (PartitionMagic clone) to partition your new drive.  Then just follow **aysiu** how-to...

---

### Post by newman on 2006-06-28
[B]
"Besides tarballing is a lot more flexible in my opinion, cause you don't waste time and space backing up useless files or even empty space..."[/B]







"**Partition Image will only copy data from the used portions of the partition.** For speed and efficiency, **free blocks are not written to the image file.** This is unlike the 'dd' command, which also copies empty blocks. Partition Image also works for large, very full partitions. For example, a full 1 GB partition can be compressed with gzip down to 400MB."

---

### Post by glinsvad on 2006-06-28
[QUOTE=newman][B]
"**Partition Image will only copy data from the used portions of the partition.** For speed and efficiency, **free blocks are not written to the image file.** This is unlike the 'dd' command, which also copies empty blocks. Partition Image also works for large, very full partitions. For example, a full 1 GB partition can be compressed with gzip down to 400MB."[/QUOTE]

Fair enough, I've never actually tried Partition Image. I just had really bad experiences using payware like Norton Ghost (under XP) because those images weren't transferable between partitions - perhaps because file allocation tables were imaged too? Glad to hear that the Linux software is more flexible this way (can't realy say I'm surprised though ;) )

---

### Post by glinsvad on 2006-06-28
Anyway, tarballing is still a better way to backup I think. Especially because the backups can be performed incrementally and with multi-volume tarballs to fit CD sizes etc..

---

### Post by newman on 2006-06-28
I actually have lots of experience with Ghost and Windows - mostly positive (with Ghost Not Windows! doh!). Annyway, I haven't tried Ghost with linux partitions because of all the horror stories I read about its compatibility with ext2/3.  I recall many years ago when I worked at a large company, we used Ghost and had some Windows 2000 and NT SID issues, so switched to Acronis which seemed to work very well.

---

