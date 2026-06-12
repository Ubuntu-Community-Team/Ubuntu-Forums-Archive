---
title: "Best Way to Reinstall OS with Separate Home Partition"
date: 2010-01-11
forum: General Help
---

### Post by slamhound on 2010-01-11
I'm on Ubuntu 9.10, 64-bit and (for various reasons) I want to do a clean reinstall.  In my initial install, I created a separate home partition, so I think the reinstall should be easy.  The one thing that I am not sure about is how the configuration files that are stored in /home are dealt with upon reinstall. For instance, I'm not sure whether these configuration files are overwritten (with the default settings) when the OS is reinstalled, or whether my current files are retained. 

Because I want to start clean, with a few exceptions, I'd prefer all the configuration files be reset to their default values when I reinstall.  So should I:

(a) just reinstall, choosing not to format /home?
(b) reinstall without formatting /home, but delete all .files and .folders before doing this (And what is the best way to do this?  Just delete all these files the last time I log into the existing setup?)?
(c) something completely different?  

Of course, I have /home backed up externally, so I could just copy the files I want back after a complete reinstall (including reformatting of /home), but I'd prefer to avoid all that copying.

Any thoughts?

---

### Post by Techsnap on 2010-01-11
> (a) just reinstall, choosing not to format /home?

Your settings will be retained and it will work similar to how you left it before you reinstalled, if you had any broken settings you'll have them again.

> (b) reinstall without formatting /home, but delete all .files and .folders before doing this (And what is the best way to do this? Just delete all these files the last time I log into the existing setup?)?

You'll have what seems like a clean install, however all your personal files will still be available to you on /home, this is probably the best option for you to use.

> (c) something completely different?

You could back up your files to another HDD, a network share or a DVD etc and restore them to /home after you reinstall.

---

### Post by J V on 2010-01-11
You could make a new partition with gparted and then move all the contents of /home over, then you don't need a reinstall at all (saves the trouble of certain config files (X, installing new apps, etc))

---

### Post by eddier on 2010-01-11
I have used option (b) several times with no ill effects.

Using the live install CD,Deleted all the .xxx files except the ones for Firefox and whatever mail client etc.

eddie

---

### Post by michy99 on 2010-01-11
> **J V said:**
> You could make a new partition with gparted and then move all the contents of /home over, then you don't need a reinstall at all (saves the trouble of certain config files (X, installing new apps, etc))

I don't see the point of this. The OP already has a separate /home partition. What is the point of making yet another one?

I usually just delete the .files and .folders for any program that isn't working right, and leave the rest alone. I had to do this for Wine in my new Karmic installation.

---

### Post by J V on 2010-01-11
oh, I thought he just wanted a home partition, my bad :)

Yes I would just delete the .files and .folders, definitley best...

Should we do this on every new install or is that ill advised?

---

### Post by Salpta on 2010-01-11
To piggie-back on this thread:

After creating another partition on the same HDD to store my data, then reformatting and reinstalling, Could I then substitute the default picture/video/etc folders in ~/ and create a hardlink to the corresponding folders in the Data storage partition so that I wouldn't have to change the default folders on all the apps?

I guess an easier way to ask it would be: Can you create Hardlinks across different partitions on the same HDD?

---

### Post by Mazin on 2010-01-11
> **Salpta said:**
> To piggie-back on this thread:

After creating another partition on the same HDD to store my data, then reformatting and reinstalling, Could I then substitute the default picture/video/etc folders in ~/ and create a hardlink to the corresponding folders in the Data storage partition so that I wouldn't have to change the default folders on all the apps?

I guess an easier way to ask it would be: Can you create Hardlinks across different partitions on the same HDD?

Use symlinks instead. It will be safer and easier to change.

---

### Post by Mazin on 2010-01-11
> **J V said:**
> oh, I thought he just wanted a home partition, my bad :)

Yes I would just delete the .files and .folders, definitley best...

Should we do this on every new install or is that ill advised?
It should be fine to keep all of your settings across installs and then simply delete certain settings if you encounter problems with certain things.  If you want to be safe, you can delete everything but the settings you want (e.g. browser settings).
The nuclear option, while the safest, is usually unnecessary.

---

### Post by J V on 2010-01-11
I mean, won't a fresh install overwrite settings?

---

### Post by features on 2010-01-11
Another way to do it, is to navigate to your home folder in the LiveCD just before installing, and rename your home directory to username.old or something like that, then install as normal, without formatting your home partition.

Then, if you need any of your files, you can copy them from username.old to username.  You also have the benefit of having a clean install.

---

### Post by michy99 on 2010-01-11
> **J V said:**
> I mean, won't a fresh install overwrite settings?

Not if you have /home on a separate partition and do not format it when you install.

---

### Post by slamhound on 2010-01-11
Great!  Thanks for all the replies; that's what I needed to know.

---

