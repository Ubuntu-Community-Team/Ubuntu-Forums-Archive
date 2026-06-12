---
title: "Help me restore deleted truecrypt partition"
date: 2010-02-16
forum: General Help
---

### Post by Snoman314 on 2010-02-16
Here's a slightly curly one.
 my /dev/sdb was a truecrypt partition that was mounted when I accidentally deleted the partition in gparted (instead of sdc, stupid). I'm pretty sure I haven't overwritten anything since then, but I'm not sure how to go about recovering this one. 
 To confound the problem, the only way I can install stuff to my ubunut machine is by downloading on a windows machine and transferring by memory stick.
 I've seen a few people saying that testdisk is good, and I'm about to try and get it installed, but any help is appreciated.

---

### Post by Snoman314 on 2010-02-16
Ok, I have successfully ( I think) mounted the decrypted partition using truecrypt and the option --filesystem=none.

still no filesystem though.

---

### Post by Richard1979 on 2010-02-16
Unmount the disk right now and boot into a live CD.
Type "sudo reboot".

Then come back here.

Reason: if you run your system with this disk mounted and being used, you may overwrite the volume headers and render the data unrecoverable.

---

### Post by Snoman314 on 2010-02-16
Oh its been unmounted the whole time. And it was a secondary partition, so I'm still running fine without it. Just all my banking details and login passwords are (nearly) lost.
 I'm accessing the web from another pc. But I'll shut it down for now on your reccomendation for now just in case.

---

### Post by Richard1979 on 2010-02-16
> **Snoman314 said:**
> Oh its been unmounted the whole time. And it was a secondary partition, so I'm still running fine without it. Just all my banking details and login passwords are (nearly) lost.
 I'm accessing the web from another pc. But I'll shut it down for now on your reccomendation for now just in case.

OK great, now you need to read this:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) :P

---

### Post by Snoman314 on 2010-02-16
Ok, I've got TestDisk running off my root partition, I've run truecrypt to get the encrypted partition mounted to /dev/mapper/truecypt1. 
 I'm now running TestDisk and have selected the truecrypt partition..
 And.. its analysing, looking for the partition I guess. This looks like it will take a while.

---

### Post by Snoman314 on 2010-02-16
Ok, cheers for that.
 The curly bit I was finding was that the volume was encrypted. Truecrypt hasn't geiven any errors, so I beleive that I have mounted a decrypted version of the volume, but that is the part that I was really shaky about. All the guides assume a regular unencrypted disk.

---

### Post by Snoman314 on 2010-02-16
Ok. Even after doing a deep scan with TestDisk, and it finding several entries of
```
  Linux                     0   16006655   16006656
```

When the scan ends there are "No partition found or selected for recovery". 
 At first it looks like its going to find a backup superblock or something, but then, nothing.
 Anyone got any ideas?

---

