---
title: "Will windows USB drives plug and play on ubuntu 8.04 server 64bit LTS ?"
date: 2009-12-27
forum: General Help
---

### Post by omingo on 2009-12-27
need some help regarding if windows USB drives will plug and play on ubuntu 8.04 LTS ?

currently using two western digital 1.5 TB, doing nightly copies from master to backup of any modified files (simple backup solution), on vista ultimate.

after I have installed Ubuntu 8.04 LTS Server (64bit), replacing vista ultimate, will I be able to just plugin these drives and setup filecopy or rsync from master to backup disk ?

---

### Post by BrettD on 2009-12-27
The short answer to this question is yes.  Almost any external USB harddrive (or memory stick) will just work under Ubuntu.  If you have any doubts before you install Ubuntu, try connecting the USB device while running the LiveCD.

If you were planning on using these drives exclusively with Ubuntu, you might want to consider reformatting them as EXT3 (the downside of this would be that you would no longer be able to read the contents of these disks from a Windows system).

---

### Post by dcstar on 2009-12-27
> **omingo said:**
> need some help regarding if windows USB drives will plug and play on ubuntu 8.04 LTS ?

currently using two western digital 1.5 TB, doing nightly copies from master to backup of any modified files (simple backup solution), on vista ultimate.

after I have installed Ubuntu 8.04 LTS Server (64bit), replacing vista ultimate, will I be able to just plugin these drives and setup filecopy or rsync from master to backup disk ?

You will have to manually mount/unmount all pluggable devices when not using a GUI (or set them up in /etc/fstab).

It will probably be easier to install the **ubuntu-desktop** package to get all the GUI features, like auto-mounting external devices.

---

