---
title: "Dropping copy speed"
date: 2009-08-23
forum: General Help
---

### Post by cristian.vrabie on 2009-08-23
Hi guys!
I recently copied a large file (6.8 GB) from one NTFS partition to an external HDD (also NTFS). The copy started with 15MBps copy speed but it slowly decreased so towards the end of the copy it was 1MBps. This was pretty bad for the estimate: at the begining it said 8 minutes, but ended up to be close to 45 minutes. Any idea why that might happen? 
Cristian

---

### Post by loomsen on 2009-08-23
> 
irrational behavior. ABORTING.

Error 0xF35B679

Please contact your local Microsoft dealer.

Do you want me to abort sending your PC's content to MS?


A Windows Forum would probably be a more appropriate place...

---

### Post by cristian.vrabie on 2009-08-23
> **loomsen said:**
> A Windows Forum would probably be a more appropriate place...

:) It did crossed my mind that the most probable cause is a NTFS problem. However I never experienced the problem in Windows, so I thought that maybe it was a mount problem. I always had slower copy speeds from/to NTFS in Linux than in Windows.

---

### Post by loomsen on 2009-08-23
From [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)
The most reasonable explanation:
> 
Interoperability

Details on the implementation's internals are not released, which makes it difficult for third-party vendors to provide tools to handle NTFS.

[...]

 Due to the complexity of internal NTFS structures, both the built-in 2.6.14 kernel driver and the FUSE drivers disallow changes to the volume that are considered unsafe, to avoid corruption.


---

### Post by aesis05401 on 2009-08-23
Out of curiosity what is happening to your memory statistics during the course of the copy?

I'm gonna be moving some large NTFS based files around in a week or two so this info will be helpful :)

---

### Post by aesis05401 on 2009-08-23
Nevermind.  This is already known - looks like it was introduced in 9.04 and has to do with the USB side of things, not NTFS. 

Here is another report from these forums:[http://ubuntuforums.org/showthread.php?t=1150108]("http://ubuntuforums.org/showthread.php?t=1150108").

Here is a roll-up on launchpad detailing jaunty's performance in this area:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337830]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337830").  It seems this issue can be worked around by using root credentials to manually mount the drives and when launching the copy process.

---

