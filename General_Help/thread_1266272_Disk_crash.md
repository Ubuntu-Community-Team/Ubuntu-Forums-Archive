---
title: "Disk crash"
date: 2009-09-14
forum: General Help
---

### Post by TheBuzzStop on 2009-09-14
I installed Wubi on my system and now the disk is not accessible.

I have 2 physical drives on my system (C & G)

The C-Drive is where I keep my critical Windows (XP) system files.
The G-Drive is where I install 90% of my applications and keep a large number of my documents and shared files.

I installed Wubi on the G-Drive and although I did not spend a lot of time testing the installed system it seemed to run okay. I rebooted the system into Windows and left the system running over the weekend so that I could access it remotely via LogMeIn.

The system was toast when I came in today.
The G-Drive appears to be  unformatted or RAW depending on what disk utility I attempt to access it with.

When I try to boot Ubuntu I get to the Grub prompt and it will not go any further.

I will say that this makes me very uneasy regarding just how benign a Wubi install is with respect to the integrity of the Windows OS that it lives with. I installed Wubi on my home system this past weekend and noticed on my way out the door this morning that the drive on which I installed Wubi was now reporting errors that required running CHKDSK to fix. NOT GOOD!

Both systems were running NTFS files systems, one system is XP-Pro and the other is Win2K.

Any suggestions as to how I might be able to recover the G-Drive?

---

### Post by Dakiraun on 2009-09-14
Hmm... well, Wubi is basically a way of embedding Linux within the existing filesystem of a drive.  What may instead have had an effect is the size of the data written to these drives if there had been any corruption on them prior to the install.  

You would be best off, I think, to grap an insteall disk for XP or Win2K and run a Chkdsk /f off of them, or possibly to also try a repair using the [System Rescue CD]("http://www.sysresccd.org/Main_Page").  It may also be worth doing some diagnostics on the hard drives themselves.

---

