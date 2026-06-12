---
title: "GRUB can't find Ubuntu after restoring image to new drive"
date: 2010-03-31
forum: General Help
---

### Post by Riverglen on 2010-03-31
I've been running a dual boot set-up with Win XP and Ubuntu 9.10.  The old 40 gb drive was showing signs of impending failure, so I replaced it with a new 120 gb drive, after saving an image of the old setup.  

After restoring the image from the original drive to the new one, Windows boots fine from the GRUB menu, but Ubuntu doesn't.  I briefly see the Ubuntu "circle" then the screen goes blank.  If I hit any key, I get a console screen of error messages (I can provide details if needed).

I think the problem is caused by the fact that the restore process scaled the saved image to fit the new, larger drive, with the result that the Ubuntu partition doesn't actually start where GRUB expects to find it.

I'd like to recover the Ubuntu installation, but if is too big a deal, I'll just wait until 10.4 is released and do a clean install.

Larry

---

### Post by johngreth on 2010-03-31
> I briefly see the Ubuntu "circle" then the screen goes blank.

This means that it did start booting up, so Grub can find it, but since it can't finish booting, the file system was probably messed up. You may still be able to recover the files from the partition, but it is unlikely that you will be able to get it to boot again.

---

### Post by Riverglen on 2010-03-31
Well, it wouldn't be much of a loss if I can't recover.  I have another copy running on my desktop machine that duplicates anything I might have lost from the laptop.  Guess I'll just wait for the new release and do a clean install.  Thanks for your response.

---

### Post by theozzlives on 2010-03-31
> **Riverglen said:**
> Well, it wouldn't be much of a loss if I can't recover.  I have another copy running on my desktop machine that duplicates anything I might have lost from the laptop.  Guess I'll just wait for the new release and do a clean install.  Thanks for your response.

Just use the live CD and copy your files to some sufficient removable media.

---

### Post by Riverglen on 2010-03-31
I guess I'm more interested in knowing what went wrong.  The attached screen shot (photo) shows what came up after the failed boot.  I didn't know what to make of it, but assumed that underlying cause of the problem was that the disk layout resulting from the image restore was different that it was on the source disk.  I may do some looking around with a live disk, but I'm too much of a Linux novice to expect to accomplish much.

---

### Post by Riverglen on 2010-03-31
Oops.  Guess it would help to actually attach the screen shot.

---

### Post by johngreth on 2010-03-31
New Story. It looks like Ubuntu is looking for the old drive by it's uuid, but cant find it because the new drive has a different uuid. Can you post the grub command to boot linux? (scroll over to button to boot ubuntu and hit 'e'). You may be able to tell ubuntu to look for the new uuid.

---

### Post by oldfred on 2010-03-31
If you start booting grub may be ok but fstab is not. Compare 
sudo blkid
to :
/etc/fstab

---

### Post by Riverglen on 2010-03-31
I've spent a little time rummaging around with the live CD and discovered a couple of things.

First, I can't mount the Ubuntu partition on the hard disk.  The error message box led me to the vol_id command.  From that, I was able to get the UUID for the partition.

Took Johngreth's suggestion to try the edit command in the grub menu, and it is trying to mount the partition, using the same UUID that I obtained from vol_id.

BUT when I then tried to boot, I got a chance to see a lot of information that had scrolled off the screen when I booted directly from the menu (as illustrated by my screen photo).  And I now find two errors that pretty much confirm that the partition is damaged:

ext3-fs error (device hda2) ext3_check_descriptors: block bitmap for group 128 not in group (block 16711717)

ext3-fs error group descriptor disrupted

So, I assume that I'm at the end of my rope?

---

### Post by johngreth on 2010-03-31
> So, I assume that I'm at the end of my rope? 

I suppose. You may be able to try again if you still have the old drive, but I can't think of any other way to get the old partition to work. You could always reinstall Ubuntu. It doesn't take that long.

---

### Post by Riverglen on 2010-03-31
Well, since a new release is about to hit the streets anyway, I guess I'll just wait for it and do a new clean install.  I haven't lost anything important.  I appreciate the help.

---

### Post by Riverglen on 2010-04-05
Well, being the stubborn type, I managed to recover from this.  Got looking around with a live CD again, and although I could not mount the Ubuntu partition from the hard drive, I was able to examine it with gparted.  Discovered that gparted has a command to check and repair a partition.  Tried it, and it worked like a charm.

---

