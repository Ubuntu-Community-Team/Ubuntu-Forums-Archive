---
title: "Small tool to verify a burned disk?"
date: 2010-03-10
forum: General Help
---

### Post by mpw on 2010-03-10
Hello,

I'm looking for a small terminal tool to verify a burned disc and compare it to an iso file.

I googled for verify burned disc/dvd - no mateches.

There is a thread, which tells how to do it in k3Burn - but I need it on terminal to use it with ssh.

Thanks for tips or links,

Bye
MPW

---

### Post by mpw on 2010-03-17
There must be any? 'Cause it's Ubuntu:-)

---

### Post by mcduck on 2010-03-17
Well, if nothing else then you could just use the "md5sum" tool to generate md5sums for the ISO and the burned disk, and compare the two.

For example like this: [http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/]("http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/")

---

### Post by john newbuntu on 2010-03-17
Just to add to what mcduck mentioned, there is a command called isoinfo that tells you the 
volume size of the image. Example:
isoinfo -d -i /dev/cdrom

Lets say the volume size is 9999.  Now, leave the CD in the player and type the following to give md5sum of the burnt iso file:
dd if=/dev/cdrom bs=2048 count=9999 conv=notrunc,noerror | md5sum

---

### Post by psusi on 2010-03-17
You don't need dd and you don't need to know the size.  You just run md5sum /dev/cdrom.

---

### Post by mpw on 2010-03-18
Thanks.

---

### Post by DawieS on 2010-03-18
If you use Brasero disk burner, click on the Tools - Check Integrity tab. You can then select the Iso file from which to do the md5sum check.:grin:

---

