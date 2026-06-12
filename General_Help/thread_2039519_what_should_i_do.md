---
title: "what should i do?"
date: 2012-08-09
forum: General Help
---

### Post by Unguidedone on 2012-08-09
On my windows partition i have a nasty rootkit called "zeroaccess" and it is quite evil.  It crashes the system with in 10 seconds of boot time when logged into the profile.  So since im duel booting i want to remove the windows section.  But there is a recovery volume that can restore it back to a fresh install.  My guess is it wont remove the rootkit and since i duel boot ubuntu/windows 7 (win7 only to play d3) it will write over the ubuntu partition if i do use the recovery option.

I could use a partition editor on the ubuntu side to kill the windows?  
(diablo 3 is not so hot in wine btw :\  but i cant play it if i cant boot into windows)
But i do need to reinstall ubuntu again so it wont be a real loss on the ubuntu side because everything is backed up and ready for a reinstall.

[https://community.mcafee.com/thread/46333](https://community.mcafee.com/thread/46333)

If i am going to destory the data on this computer to get rid of the rootkit and make use of the wasted windows space i need a way to security wipe the drive.  on my ubuntu 10.10 computer i had a command that i could use if my house got raided it was : (if your reading this do not run this command it wipes the computer)  but i used: sudo shred /dev/sda -n 7  (what is the 12.04 equivalent command?)  I have also read that even if i do wipe the drive and install fresh that it could be still there?

Is it worth saving the windows partition and having to reinstall ubuntu or just making ubuntu the default os?

ideas?
ideas?
im going to bed thanks for any help with this matter ):P

---

### Post by Bucky Ball on 2012-08-09
If you're just wanting to resize partitions then resize XP and Ubuntu partitions with Gparted (Ubuntu's partition editor. If you are using anything newer than XP resize the Windows partition with the Windows software (that is in there already).

To resize Ubuntu partitions, boot from a livecd, launch Gparted, right click and make sure the partition you want to resize is unmounted, right click and resize it. 

I advise backing up anything, if there is anything, you don't want to use before commencing. This process shouldn't kill anything but nothing's perfect. ;)

(Not sure if Win recovery will wipe the drive. Doubt it will have any idea what the Linux EXT* partitions are, apart from healthy.)

---

### Post by Unguidedone on 2012-08-09
any more ideas before i start?

---

### Post by Habitual on 2012-08-09
backups?

---

### Post by Unguidedone on 2012-08-09
everything is fully backed up :D

---

### Post by cryptotheslow on 2012-08-09
If it is a SATA drive you could try using hdparm to do a security erase or enhanced erase. This is a drive firmware level function that securely erases all user blocks on the drive as well as having options for taking out hidden data sectors which an operating system typically can't access.

Read the hdparm manpages very carefully before considering using it - it has some very dangerous options.

Note - this method of erasing will remove all your partitions and more.

There's a brief walkthrough here:
[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)

But please do your own research before commencing down that path.

---

