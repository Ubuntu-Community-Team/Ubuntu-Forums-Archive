---
title: "Can't Seem to Get rid of Ubuntu 10.04"
date: 2010-08-23
forum: General Help
---

### Post by jikong414 on 2010-08-23
Hello, I recently decided to purchase a new laptop and I ordered one online. Sadly when I started it up it wasn't a Windows, but an ubuntu. So I was really confused.

I never seen an ubuntu laptop before so I was surprised and tried flickering around with it but I found it wayyyy too difficult to operate and tried installing windows xp.

I went to the BIOS and reset the boot order as XP CD first, but when I tried booting with it, my computer came up with another problem where my hard drive wasn't found...

but my laptop came with 70GB harddrive

I read throughout the forum for some answers, but whenver I read them it's just too complicated for someone like me to understand. So I'm really confused and was wondering if you guys can give me like a dummy version of the solution

---

### Post by ubudog on 2010-08-23
Boot the live cd, use gparted to format the hd.  Then use the windows install disk to reinstall windows.

---

### Post by jikong414 on 2010-08-23
> **ubudog said:**
> Boot the live cd, use gparted to format the hd.  Then use the windows install disk to reinstall windows.

Sorry if I sound too stupid but what do you mean by boot the live cd? Do you mean the windows CD??

---

### Post by ubudog on 2010-08-23
No, get an Ubuntu cd and start it in the computer.  Instructions on ubuntu.com.

---

### Post by -kg- on 2010-08-23
No, he means the Ubuntu Live CD, or alternatively the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php").

Are you using Ubuntu to post here or another computer?  With either, you can download either the Ubuntu Live CD iso from this site (I would suggest using a torrent for speed and error checking), checking the md5 checksum (checks that the download was successful and not corrupted), then burning the .iso to a CD-R.

Alternatively, you can order an Ubuntu Live CD from Canonical (it will take some time to get to you) or get one at a local computer shop (like Best Buy, if you're in the U.S.).  You can also use a third party partitioning tool, if you have access to one that will handle Linux partitions.

What you're trying to do is erase all the (Linux) partitions on your hard drive and leave it with all free space on which your XP installation disk will create its own partition and install XP.

If it's not too much for you, you can find out more about basic partitioning operations at the link in my signature block below.

---

### Post by wilee-nilee on 2010-08-23
You will have to go into the bios and set the hardrive to IDE unless you have the sata drivers for XP. Also XP wont install to a NTFS partition that gparted builds. 

So reset the bios and boot the XP cd and your HD should be there.

---

