---
title: "EXT4 questions prior to 9.10"
date: 2009-08-13
forum: General Help
---

### Post by AwesomeTux on 2009-08-13
Hello,

I am wondering if I could make a new partition on my drive, format it to EXT4, and just move everything over to it, and have it work?

When Ubuntu 9.10 comes out is this the process I'll have to do in order to use EXT4 in 9.10 from 9.04?

What is the safest way of going from EXT3 to EXT4?

Thank you.

---

### Post by P4man on 2009-08-13
[http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html](http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html)

Id strongly recommend you just stick to Ext3 though, there is no compelling reason to change. If ever you're doing a fresh install, you might use the opportunity to format as Ext4, but even then Id be in no hurry.

```
What is the safest way of going from EXT3 to EXT4?
```

Safest is staying where you are :)

---

### Post by XCan on 2009-08-13
Safest way is as you said yourself. Create the ext4 partition, and move your existing data over to it. You could of course push your data to an external backup media or something and just redo your current partition(s).

I think there is some kind of tool to convert ext3 to ext4, but as always with these tools, you still better backup the important data anyway. Besides, I haven't seen any tests showing 'must-have' boosts with ext4 compared with ext3.

---

### Post by fennec_fox on 2009-08-13
Maybe this isn't the easiest per say but, this is what I would do personally. Back up all of your data/files/themes and programs onto an external drive, make a list of what programs you had installed, then install a fresh system with ext4 and move everything back. This way you can get the entire drive into ext4, no conversions or anything and if any of the programs stop working for some reason you have a list of the ones you had. 

This is pretty much the same as your ext4 idea but, I just feel as if there could be problems with system files moving them from ext3 to ext4, probably not but, I'd be paranoid of that. 

Though, what gain do you want to get from ext4? Ext3 may not be as fast or anything but, you might not get enough gain to make it worth your time. I'd just do it when you upgraded or reinstalled.

---

### Post by AwesomeTux on 2009-08-14
> **fennec_fox said:**
> Maybe this isn't the easiest per say but, this is what I would do personally. Back up all of your data/files/themes and programs onto an external drive, make a list of what programs you had installed, then install a fresh system with ext4 and move everything back. This way you can get the entire drive into ext4, no conversions or anything and if any of the programs stop working for some reason you have a list of the ones you had. 

This is pretty much the same as your ext4 idea but, I just feel as if there could be problems with system files moving them from ext3 to ext4, probably not but, I'd be paranoid of that. 

Though, what gain do you want to get from ext4? Ext3 may not be as fast or anything but, you might not get enough gain to make it worth your time. I'd just do it when you upgraded or reinstalled.

Mainly for the speed, but also block mapping extents, pre-allocation, allocate-on-flush (delayed allocation), subdirectory limit, Journal checksumming, faster file system checking, and multiblock allocator.

Pretty much the whole kit and caboodle.

And I plan to re-install Ubuntu when Ubuntu 9.10 comes out, installing it on the new EXT4 partition, and moving everything over.

---

