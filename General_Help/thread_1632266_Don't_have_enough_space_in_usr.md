---
title: "Don't have enough space in /usr"
date: 2010-11-27
forum: General Help
---

### Post by TectonInd on 2010-11-27
Here's my problem:

Recently I tried installing updates, only to find that I didn't have enough space in /usr. I was also unable to download and install any packages. I had two partitions; one to store Ubuntu and Windows XP, and the other for everything else. I resized both partitions, tripling the space on the OS partition, but I STILL RECEIVED THE SAME ERROR. Both drives are formatted with NTFS.

The error message from update manager is as follows:

The upgrade needs a total of 505M free space on '/usr'.
Please free at least am additional 505M of disk space on '/usr'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Keep in mind that I have emptied the trash bin, and I ran clean.

What is causing this? What is a solution? How do I prevent problems like this in the future? Any help or insight would be greatly appreciated.

---

### Post by TectonInd on 2010-11-27
bump

---

### Post by oleink on 2010-11-27
> **TectonInd said:**
> Here's my problem:

Recently I tried installing updates, only to find that I didn't have enough space in /usr. I was also unable to download and install any packages. I had two partitions; one to store Ubuntu and Windows XP, and the other for everything else. I resized both partitions, tripling the space on the OS partition, but I STILL RECEIVED THE SAME ERROR. Both drives are formatted with NTFS.

The error message from update manager is as follows:

The upgrade needs a total of 505M free space on '/usr'.
Please free at least am additional 505M of disk space on '/usr'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Keep in mind that I have emptied the trash bin, and I ran clean.

What is causing this? What is a solution? How do I prevent problems like this in the future? Any help or insight would be greatly appreciated.

Take a look:
[http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1290903785208+28353475&threadId=625859](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1290903785208+28353475&threadId=625859)

[http://www.unix.com/advertisement.php?url=http://www.unix.com/showthread.php?t=6643](http://www.unix.com/advertisement.php?url=http://www.unix.com/showthread.php?t=6643)

---

### Post by dcstar on 2010-11-27
> **TectonInd said:**
> Here's my problem:

Recently I tried installing updates, only to find that I didn't have enough space in /usr. I was also unable to download and install any packages. I had two partitions; one to store Ubuntu and Windows XP, and the other for everything else. I resized both partitions, tripling the space on the OS partition, but I STILL RECEIVED THE SAME ERROR. **Both drives are formatted with NTFS**.
.........

Ubuntu **cannot** be installed on a NTFS partition, so you need to clearly explain exactly what your setup actually is.

---

