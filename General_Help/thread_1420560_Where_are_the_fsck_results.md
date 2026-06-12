---
title: "Where are the fsck results?"
date: 2010-03-03
forum: General Help
---

### Post by donsy on 2010-03-03
I forced a fsck on the next boot by
```
sudo touch /forcefsck
```
Where did the results go? /var/log/fsck/checkfs and /var/log/fsck/checkroot both read "(Nothing has been logged yet.)" Am I to assume that if there are no errors nothing is written to the log files?

---

### Post by donsy on 2010-03-03
I thought it was a fairly simple question.

---

### Post by JKyleOKC on 2010-03-03
Here's what I see in checkfs:
```
Log of fsck -C -R -A -a 
Sat Feb 13 12:22:26 2010

fsck 1.40.8 (13-Mar-2008)
/dev/sda7: clean, 7770/16269312 files, 33749396/65065250 blocks

Sat Feb 13 12:22:28 2010
----------------
```February 13 was the most recent reboot of this system. The checkroot log is similar.

---

### Post by donsy on 2010-03-03
> **JKyleOKC said:**
> Here's what I see in checkfs:
```
Log of fsck -C -R -A -a 
Sat Feb 13 12:22:26 2010

fsck 1.40.8 (13-Mar-2008)
/dev/sda7: clean, 7770/16269312 files, 33749396/65065250 blocks

Sat Feb 13 12:22:28 2010
----------------
```February 13 was the most recent reboot of this system. The checkroot log is similar.

Thanks for your reply. According to your profile you're running Hardy 8.04. I wonder if Karmic 9.10 has a different way of logging the results?

---

### Post by JKyleOKC on 2010-03-03
That's possible; Karmic may be using ext4, also, whereas I'm using ext3, and that could make a difference.

---

### Post by deadlockedgamer on 2010-03-03
If there is any errors it will ask if you want to try and fix them, if not assume there was no error! Karmic has a built in tool that tell you when a disk is failing which I used to find what was causing issues with my comp!

---

### Post by chronniff on 2010-05-14
Hey saw your post as I was just thinking the same thing....I noticed this a few releases ago, for some reason somewhere along the way the auto filechecks stopped logging their results...don't know whether this was by design or overlooked, but I can't find the results in any of the logs....I am now running ubuntu lucid, same thing....quite perplexing, and slightly irritating

---

### Post by chronniff on 2010-05-14
Spoke to soon, just found the results in /var/log/boot.log, the relevent lines for me were:

dev/mapper/vg0-lv1--root has been mounted 20 times without being checked, check forced.
/dev/mapper/vg0-lv2--home: clean, 79621/43712512 files, 59580273/174820352 blocks (check in 2 mounts)
/dev/mapper/vg0-lv1--root: 240669/1831424 files (0.1% non-contiguous), 2028792/7323648 blocks


This is what happens when a distro decides to completely reinvents the boot process, nobody has any clue what is actually happening under the fancy new boot splash screens...I'm happy for the improvements that they have made to boot up times and such, but if your going to throw out a system that has been around for probably over a decade, the least the ubuntu devs can do is document the hell out of all the changes, and why they were changed, and at the very least, where things have been moved around to.

---

### Post by Ron O on 2010-05-15
chronniff- Lucky you!  My dev/mapper directory is empty, and I've run touch fsck a half dozen times- it runs at boot but no log that I can find.

I agree with all in your last paragraph.

---

### Post by Ron O on 2010-05-15
Sorry. Misread the path and went to /dev/mapper instead of /var/log/boot.log. But I only found an entry for the system generated fsck and nothing for the latest that I initiated with the touch command. Still agree with your last paragraph.

---

