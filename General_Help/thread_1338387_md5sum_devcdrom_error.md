---
title: "md5sum /dev/cdrom error"
date: 2009-11-26
forum: General Help
---

### Post by isee on 2009-11-26
Hello!

I'm trying to install a clean 9.10 from a LiveCD bitTorrent download, but ran into a continuous error, and had to power off the computer.
Thought I'd try a checksum on the CD, following instructions from here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

but got an error

commander@gateway-laptop:~$ md5sum /dev/cdrom
md5sum: /dev/cdrom: Input/output error.

Should I try another download?

---

### Post by bodhi.zazen on 2009-11-26
md5sum the downloaded iso first.

If the iso is OK, then burn again.

You may also wish to confirm the CD drive works by testing a known good CD.

---

### Post by isee on 2009-11-26
Thanks much bodhi.zazen.  It was a bad download.  I got another and the sum was equal, and it installed np.

An aside, I ran md5sum on the CD after I burned the new download, and it was different on the CD
8790491bfa9d00f283ed9dd2d77b3906  desk-top iso 
2a22a3bff98fd0d15fe4387753eab0f3  cd burn

but it installed np.  Is that correct?  Does burning change the sum?

---

### Post by StuartN on 2009-11-26
I had a different experience - I downloaded the 9.10 Desktop ISO, then double-clicked the ISO in Nautilus to bring up Brasero, burned a CD (three, actually) and received an error during the checking phase.

The ISO file (both downloads, actually) checked correctly.

The CD (well, all three) also checked themselves correctly.

Ubuntu 9.10 installed from the CD.

I conclude that there is something a bit iffy about the checking process in the Brasero in the Ubuntu 9.04 standard install from which I attempted to burn the ISO file.

---

