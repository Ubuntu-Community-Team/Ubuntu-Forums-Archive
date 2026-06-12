---
title: "Secondary hard drive won't boot..."
date: 2006-02-13
forum: General Help
---

### Post by Dann7391 on 2006-02-13
So I am completely new to 5.10...but have had some experience with 5.04. I have one 80gb SATA hard drive that has grub on it with ubuntu 5.10 and win XP. During the installation I didn't want to take the chance of messing up my NTFS 250gb SATA hard drive, so i unplugged it. Now that ubuntu is installed I want to plug it in so I can access its files from ubuntu...when I plug it in and then start up the computer, GRUB loads and then I pick ubuntu and then it goes to the loading modules type screen then gives a black screen with alot of white processing text and then says something like "Error: dev/sda not found"

I THINK!. ANyway I really want to fix this..anyway I can do without formatting or reinstalling? I have a feeling that if the hard drive were plugged in during installation that it would recognize it.

---

### Post by KnottyMan on 2006-02-13
Sounds like the 250 is detected before the 80.  Your "drive letters" have moved and Ubuntu can't find it's root disk.

Make the 80 show first and it'll work.

---

### Post by Dann7391 on 2006-02-13
Care to explain how?

---

### Post by KnottyMan on 2006-02-13
Depends on your controller.  Just like in IDE land, primary master comes before primary slave, sata usually has port 1, port 2, etc.  The 80 should be on port 1.

In your POST, it should also list the drive order.

On some BIOSes, you can specify which drive is your boot drive.  Might also try that.

---

### Post by Dann7391 on 2006-02-13
Did everything I could with switching the ports...I still get that error...copied it down this time.

"Booting the kernel.
Loading please wait......

ALERT! /dev/sda2 does not exist. Dropping to a shell!"

Would it be easier for me to reinstall Ubuntu 5.10 while having the 250GB plugged in?

---

