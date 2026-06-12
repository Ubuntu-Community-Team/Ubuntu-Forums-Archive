---
title: "Windows-installed version problems: GNOME removed - advice please"
date: 2010-07-06
forum: General Help
---

### Post by printf() on 2010-07-06
I installed karmic using the windows installer about 4 or 5 months ago.

I was forced to hard crash the system during a software update which lead to not being able to load the desktop environment (the windows installer is apparently famously unstable during power loss).

Trying to fix this I took actions which eventually completely removed GNOME from the system. After booting it now goes directly into GRUB.

I still have the root.disk file in C:\ubuntu\disks, so my files are still intact. Do you know how I can either access these files from windows (can you mount this virtual disk somehow?) or repair the installation to get GNOME back?

I want to get the files off of the root.disk file, uninstall this version of ubuntu, then install lucid properly on a separate partition.

Any suggestions on how I can go about doing this?

---

### Post by printf() on 2010-08-11
I'm sorry to bump an old thread. Does anyone have any ideas?

---

### Post by Elfy on 2010-08-11
have you tried any of these methods?

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

not usre I can help in any other way I'm afraid

---

### Post by printf() on 2010-08-11
Thank you very much for your help. These forums are incredibly useful.

I will try these methods and post back here later.

---

### Post by printf() on 2010-08-11
I have just managed to access all of my files using the 'ext2read' software which I found in the link you provided.

Anyone who is having a similar problem go here: [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/) I think it also comes under the name 'ext2explore', which I think may be the name of the explorer-type component of the software.

Thank you for your support forestpiskie.

---

