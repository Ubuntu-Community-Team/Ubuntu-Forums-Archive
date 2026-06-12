---
title: "$MFTMirr does not match $MFT (record 0)."
date: 2009-11-24
forum: General Help
---

### Post by John Long on 2009-11-24
I'm unable to mount my extra drive. Any ideas what I should do?

multimedia@johnny-desktop:~$ sudo mount /dev/sda1
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by dcstar on 2009-11-24
> **John Long said:**
> I'm unable to mount my extra drive. Any ideas what I should do?

multimedia@johnny-desktop:~$ sudo mount /dev/sda1
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Do a fsck on it.

---

### Post by John Long on 2009-11-24
This is what I get.


```
multimedia@johnny-desktop:~$ fsck /dev/sda1
fsck from util-linux-ng 2.16
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda
```1

---

### Post by John Long on 2009-11-25
I went into Synaptic Package Manager and reinstalled ntfs-3g but still no luck. I'm receiving the same error.

---

### Post by jacobs444 on 2009-11-25
if you can boot into windows, you need to do an MSoft scandisk on it, then you should be able to mount. Used to have the same problem, and thats how I fixed. Also if that alone doesn't work then do a defrag.

---

### Post by John Long on 2009-11-25
What if I have no windows partition?

---

### Post by anonSam on 2009-11-25
I had this exact same problem a few weeks ago too. It was caused by unplugging the drive while it was still writing something. I ended up plugging it into a Vista machine, defraged it then ran scandisk (or is it chkdisk? I can't remember...). Just plug it in and right click on the drive and I think its either that menu or under Properties. It's easy to find. Anyway it found 4 messed up pictures I ended up having to delete. After that it worked like new.  If you have no windows partition ask a friend with windows or you could take it to a computer shop and have them do it. It took around an hour to finish on an almost full 750GB drive.

---

### Post by dcstar on 2009-11-25
> **John Long said:**
> This is what I get.


```
multimedia@johnny-desktop:~$ fsck /dev/sda1
fsck from util-linux-ng 2.16
fsck: **fsck.ntfs-3g: not found**
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda
```1

You need to install the **ntfsprogs** package.

---

### Post by John Long on 2009-12-05
Is there a way I could boot to free-DOS from a CD or USB and run scandisk from there?

---

### Post by msr1985 on 2013-01-31
what i do:

1- ```
sudo apt-get install ntfsprogs
```

2-  ```
 sudo ntfsfix /dev/sdb1 
```

I hop it works for you.:)

---

### Post by codemaniac on 2013-01-31
Old thread is closed now.
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

