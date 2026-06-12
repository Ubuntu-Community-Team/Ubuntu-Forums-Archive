---
title: "Problem mounting TrueCrypt volume"
date: 2009-08-23
forum: General Help
---

### Post by Eladon on 2009-08-23
I have a server running Hardy with Samba shares, and a desktop that was running Hardy until I recently reloaded it with Jaunty and formatted the drive ext4.  I have a 2GB TrueCrypt volume (file) located on my server that I have been opening and using from my desktop computer without troubles for a long time.

So I went to mount the volume (first time) on my newly reloaded desktop, and I get the following error message:
```
Input/output error:
/dev/mapper/truecrypt5

The drive is damaged (there is a physical defect on it) or a cable is damaged, or the memory is malfunctioning.

Please note that this is a problem with your hardware, not with TrueCrypt. Therefore, please do NOT report this as a bug/problem in TrueCrypt and please do NOT ask for help with this in the TrueCrypt Forums. Please contact your computer vendor's technical support team for assistance. Thank you.

Note: If the error occurs repeatedly at the same place, it is very likely caused by a bad disk block, which should be possible to correct using third-party software (note that, in many cases, the 'chkdsk /r' command cannot correct it because it works only at the filesystem level; in some cases, the 'chkdsk' tool cannot even detect it).
```
So to test if there really was a problem, I opened a terminal into the server, and made a copy of the TrueCrypt volume, and it was successful.  Then back on my desktop I tried mounting the copy of the volume, and it mounts successfully! (OK, now I'm confused).
Then, to thicken the plot, I fired up a third computer which I had Windows XP on, and tried mounting the original (theoretically corrupt) TrueCrypt file, and it mounted fine.

All computers are running TrueCrypt 6.2a

None of this seems logical, I'm just not sure how to proceed.  Can I trust this Jaunty + TrueCrypt combination, or is it going to start corrupting my volumes?  I guess my question is, what would you do next if you were in my situation?

---

### Post by michy99 on 2009-08-23
According to the error message, the problem is with the disk, not with truecrypt or jaunty.

---

### Post by Eladon on 2009-08-23
Understood, except I was able to copy the file without issue (which is not usually the case when you have a sector problem on your hard drive), and I was able to mount the file without issue with the exact same version of software, except from Windows XP, and it didn't complain at all.

So just to check, I dug out an old desktop that I had Hardy installed on, loaded it up, installed TrueCrypt 6.2a on it, and opened the volume, again without issue, no error messages.  So what?  Does Jaunty have some magical capability to detect bad sectors on hard drives that are on a completely different computer, such that it can feed this info to a third party program, yet neither Hardy nor Windows XP (nor the server itself) seem to have any problem with this file at all?

---

### Post by Eladon on 2009-09-05
I noted the fix to this problem in the following post:

[http://ubuntuforums.org/showthread.php?p=7900185#post7900185](http://ubuntuforums.org/showthread.php?p=7900185#post7900185)

---

