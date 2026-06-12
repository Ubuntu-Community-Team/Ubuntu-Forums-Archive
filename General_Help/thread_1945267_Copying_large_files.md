---
title: "Copying large files"
date: 2012-03-22
forum: General Help
---

### Post by aeronutt on 2012-03-22
So I had a few large files to copy, about 5GB each. From/to same partition. Start the copy, it says '3 minutes left', so I think....a quick solitare game. And poof...system hangs. Nada. Nothing. I wait about 5 minutes, and nada...mouse is obviously not working. Power down, reboot. And of course the new directory I was copying to doesn't even exist after a reboot. Really?

Is there a known problem using nautilus to copy large files?
Better way?

---

### Post by jayshomebrew on 2012-03-23
```
rsync -av --progress /path/to/source/directory /path/to/target/directory
```

works great for me..

[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

[http://www.cyberciti.biz/faq/show-progress-during-file-transfer/]("http://www.cyberciti.biz/faq/show-progress-during-file-transfer/")

---

### Post by dcstar on 2012-03-23
> **aeronutt said:**
> 
........
Is there a known problem using nautilus to copy large files?
Better way?

Yes, but it depends on your hardware and Ubuntu version. This can help:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by 3rdalbum on 2012-03-23
> **aeronutt said:**
> So I had a few large files to copy, about 5GB each. From/to same partition. Start the copy, it says '3 minutes left', so I think....a quick solitare game. And poof...system hangs. Nada. Nothing. I wait about 5 minutes, and nada...mouse is obviously not working. Power down, reboot. And of course the new directory I was copying to doesn't even exist after a reboot. Really?

Is there a known problem using nautilus to copy large files?
Better way?

No, it should work.

If the whole computer is crashing while copying a large file, then chances are that you've got faulty RAM. Linux tries to cache as much of the file as possible in available memory, so copying a file is actually a very good test of if your RAM is working correctly.

Try removing your RAM sticks and putting them back in. If this doesn't help, try removing one stick and see if the problem happens - if not, then the stick you took out is bad. If the problem still occurs, then it must be the other RAM stick that's faulty.

---

### Post by sudodus on 2012-03-23
> **3rdalbum said:**
> No, it should work.

If the whole computer is crashing while copying a large file, then chances are that you've got faulty RAM. Linux tries to cache as much of the file as possible in available memory, so copying a file is actually a very good test of if your RAM is working correctly.

Try removing your RAM sticks and putting them back in. If this doesn't help, try removing one stick and see if the problem happens - if not, then the stick you took out is bad. If the problem still occurs, then it must be the other RAM stick that's faulty.

I suggest that you run ***memtest*** from the grub menu. This will test your RAM thoroughly if you let it run overnight.

I guess that you have checked that you have enough free space in the partition, where you want to copy the big files.

You can also check the file system. Boot a live session from a CD or USB drive, for example your Ubuntu install drive. Unmount the partition and then run
```
e2fsck -f /dev/sd[COLOR="Red"]xy[/COLOR]
```
where [COLOR="red"]x is a[/COLOR] for the first drive and [COLOR="red"]y is 1[/COLOR] for the first partition etc.

---

### Post by aeronutt on 2012-03-23
Thanks folks, great ideas. 
Enough space on partition: Yes, ok.
File system check: Yes, ok.
Using rsycn: I'd thought of that...but should I need to?
Memtest: Great idea, will do!!

---

### Post by sudodus on 2012-03-23
If memtest shows that the RAM is OK, I suggest that you

1. try *[dcstar]("http://ubuntuforums.org/member.php?u=7532")*'s link (to edit a few lines according to the instructions for Ubuntu) and/or

2. try ***rsync*** or finally

3. try with a live session booted from an install CD or USB drive with the newest version (beta Precise) of [KLX]Ubuntu.

---

