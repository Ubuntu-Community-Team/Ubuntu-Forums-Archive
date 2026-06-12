---
title: "Unable to access ubuntu drive from windows"
date: 2010-01-09
forum: General Help
---

### Post by tharpa on 2010-01-09
I recently switched to Ubuntu from OpenGeu.  I have Ubuntu on my external drive, and Windows Vista on my hard drive.  I dual boot with Grub.  

When I had OpenGeu, I was only able to have read-only access to my Windows drive from Linux, but I had read-write access to my Linux drive from Windows.

Ironically, I now have read-write access of my Windows drive from Ubuntu, which is good, but I can not access my Ubuntu Linux drive from Windows at all.  (I get one of those scary "The drive is not formatted.  Click Yes to format.")

Any suggestions on how I can access my Ubuntu drive from Windows Vista?

Thanks.

---

### Post by Tim Sharitt on 2010-01-09
If your ubuntu drive is formatted as ext2 or ext3 (ext3 is the default in the current version of ubuntu) you can use the Ext2 IFS driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) (which is closed source) or Ext2Fsd from [http://www.ext2fsd.com/](http://www.ext2fsd.com/) (which is open source).

---

### Post by tharpa on 2010-01-09
> **Tim Sharitt said:**
> If your ubuntu drive is formatted as ext2 or ext3 (ext3 is the default in the current version of ubuntu) you can use the Ext2 IFS driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) (which is closed source) or Ext2Fsd from [http://www.ext2fsd.com/](http://www.ext2fsd.com/) (which is open source).

I tried both of those, but they didn't work for me.

---

### Post by Jackzor on 2010-01-09
As far as I know you can't? That is why I made a ntfs drive to use for both OS's

---

### Post by michy99 on 2010-01-09
Actually, ext4 is the default in 9.10 if you do a fresh install.

---

### Post by tharpa on 2010-01-09
> **michy99 said:**
> Actually, ext4 is the default in 9.10 if you do a fresh install.

Well, my drive is showing up as ext3.  Maybe because OpenGeu uses Ubuntu 8.10.

---

