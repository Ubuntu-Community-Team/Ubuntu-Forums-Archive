---
title: "USB and superblock...???"
date: 2010-07-11
forum: General Help
---

### Post by robertcoulson on 2010-07-11
Hi...Trying to mount my USB stick and getting a superblock error..Tried a command in the terminal but it said only "ROOT" can access command...How do I get to "ROOT"...???...See attachment.
Robert

---

### Post by JustinR on 2010-07-11
Type sudo in front of the mount command.

---

### Post by CharlesA on 2010-07-11
If it's fat32, it would be -t vfat.

---

### Post by robertcoulson on 2010-07-11
Thanks...But the command I tried to use didn't work...Guess my superblock is defective on my USB stick...Guess I lost ALL my pics on it.
Robert

---

### Post by CharlesA on 2010-07-11
What is it saying when you run that command?

---

### Post by robertcoulson on 2010-07-11
Well tried your info,(SEE ATTACHMENT)..Guess maybe my stick is bad...Thanks for trying to help me.
Robert

---

### Post by CharlesA on 2010-07-11
No, it's not bad, just means that the folder you are trying to mount to doesn't exist. Try this:

```
sudo mount /dev/sdb1 -t vfat /cdrom/
```

Then cd to /cdrom/ and get yer pictures. :)

---

### Post by JustinR on 2010-07-11
You have to create the folder in /media first before you try to mount the USB flash drive to it.

Ubuntu, by default, uses /media instead of /mnt.

---

### Post by robertcoulson on 2010-07-11
Here is what I get..see attachment
Robert

---

### Post by JustinR on 2010-07-11
Try mounting it in Windows. If that doesn't work then I'm not sure what else you can do.

---

### Post by robertcoulson on 2010-07-11
Hey JustinR...Your killing me man...I barely understand what you are saying, let alone try what you are saying (ha,ha).
Robert

---

### Post by robertcoulson on 2010-07-11
Sorry about double post..tried to see it in windows and a 2nd Ubuntu computer and get the same thing.
Robert

---

### Post by CharlesA on 2010-07-11
If it doesn't work in Windows, try running chkdsk on it from there.

---

### Post by robertcoulson on 2010-07-11
Hi CharlesA...I think I tried that a couple of days ago and got nowhere...Maybe, just maybe do you think my 16gb stick is defective,,,???
Robert

---

### Post by CharlesA on 2010-07-11
Could be. It's just a regular Memory stick?

Could try something like photorec or testdisk I guess to see if you can pull the data off of it.

---

### Post by robertcoulson on 2010-07-11
downloading TESTDISK..If I can get my pics off of it, then I can throw it in the garbage...thanks for the info.
Robert

---

### Post by robertcoulson on 2010-07-11
Thank you, thank you, thank you...TESTDISK is letting me copy my pictures to a folder...Works great..Thanks again.
Robert

---

### Post by JustinR on 2010-07-11
Usually a bad superblock means a corrupted partition table. Formatting will fix the problem.

---

### Post by CharlesA on 2010-07-11
Awesome. Try reformatting it and see if it will mount.

---

### Post by robertcoulson on 2010-07-11
Only, and I mean only after I get ALL my info off it..Testdisk takes time, will have to continue tomorrow...Thanks very much.
Robert

---

