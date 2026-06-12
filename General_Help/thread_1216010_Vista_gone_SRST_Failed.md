---
title: "Vista gone? SRST Failed?"
date: 2009-07-17
forum: General Help
---

### Post by Gizenshya on 2009-07-17
This is completely Random.  I got this message from Vista that said "To apply changes a restart is needed.  restart now? later?" (or something to that effect).  I dismiss it, but needed to go to ubuntu, so I restarted.

Then, the splash screen for my mobo stays on for waaay too long (uysually about a second, now about 30).  Then I get a mesage:

"SRST Failed."  "errno=-16" and some other stuff, but I think that was the most important.

Well... Vista is gone now.  There is no grub boot menu anymore.  Ubuntu just boots immediately without any other option.

any ideas what happened?  How do I fix this?

if you need any more information, just let me know.

---

### Post by Gizenshya on 2009-07-18
I haven't been able to find out what's going on.  It keeps giving me different messages and errors.

Vista came back, but my sdb1 wouldn't mount.  I tried several times.  So, I restarted, and the disk checker said something hadn't been checked in 25 boots, so it checked it.  Then I got tons of errors in text that flooded the screen. when I tried to boot.

So, I restarted again.  This time everything seemed normal, BUT when I tried to move files from sda1 to sd**b**1 (about 15 giga), it moved 208 kb and it is stuck.  Nothing is frozen.,.. just nothing is transferrring.  Since I moved them , I'm afraid to hit cancel, because it may result in files losses.

Any ideas?

---

### Post by jerome1232 on 2009-07-18
To me it sounds like hardware issues with your HDD or the SATA controller, or even *possibly* your power supply isn't putting out enough power?

---

### Post by Gizenshya on 2009-07-18
How would I figure out which?  I really doubt it is the hard drive.  It is only about 9 months old or so (1tb caviar black).  It is hooked up internally, though it is only mounted to transfer files to it.  Otherwise it is unmounted (and it turns itself off).

On a possibly related note, Vista stopped recognizing the drive a months or two ago, giving no reason.  It sees that a drive is there, but refuses to interact with it.  The whole time Ubuntu has been using it fine, though.

ATM, it is about 500 mb into that transfer from before, saying it has umpteen hours left at a few hundred kbps.  I think it's going in bursts, with long periods of nothing...

how would I figure out the root problem?

edit: I copied the fiels to the same drive, so I would have a backup, and copied what files back that were already copied.  That kept me from having any data loss.  But, when I tried to restart again, it said that it is against system policy to reboot with multiple users logged in.  wtf?  I have no idea what that means :(  But the computer isn't hooked up to any network, much less the internet.  and I never ran a command prompt during that session or anything, so I don't know where it is geting the other user.  I took a screenshot and sudo rebooted it.

if anything changes, I'll update again.

---

### Post by Gizenshya on 2009-07-18
I restarted to try to play some music on it, and it would work, then freze, then work, and so on.  Then it wouldn't hardly work anymore, so I unmounted it, and tried to mount it again.  The error message it gave is attached.

:'(

---

