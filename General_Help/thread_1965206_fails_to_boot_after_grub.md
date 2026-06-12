---
title: "fails to boot after grub"
date: 2012-04-25
forum: General Help
---

### Post by buffchick on 2012-04-25
So, no changes. no updates. Everything has been working fine. I went to reboot and grub shows up and bam. Nothing. alt-f2 doesn't get me anywhere. Nothing happens. I hit ctrl-alt-del and it restarts and brings me back to grub. I can't get the kernel to load and I"m not sure what the next step should be. I'm not familiar enough with how linux loads. Suggestions?

---

### Post by corrytonapple on 2012-04-25
First, what is your computer model/brand?
What do you see when you select your operating system, or if you even see GRUB at all?  If you get past GRUB, what do you see then?  Hit the "PRTSC" key and it will display what is actually happening as the system should be loading.  If PRTSC doesn't work, try using "Pause/Break" key or "INS" key.  If you still get nothing, then try booting into recovery mode.  If you can get to that, tell us and we can go from there.

---

### Post by buffchick on 2012-04-25
I see nothing. couldn't get to recovery mode either. Added "noapic" jsut after quiet spalsh to boot options and it loads. Not sure where to go next it was just something I found googling and thought I'd try.

Oh, and it's old old old. which is why I went with Xubuntu. It's a Dell Optiplex GX150 with 512mb ram. has two SATA pci cards and an AGP card. has mouse and keyboard.

---

### Post by corrytonapple on 2012-04-25
So since you added that line in GRUB, you say you can see the desktop?  If so, then this sounds like a GRUB related issue.  Like it isn't doing something right.

---

### Post by buffchick on 2012-04-25
The problem seems to reoccur when I hook my svideo connection back up. and noapic doesn't help.

---

### Post by corrytonapple on 2012-04-25
That suggests something else then.  Boot up with nothing connected, and see if it works.  If it is a desktop, that means just the power cord in the wall and the monitor hooked up.  If it is a laptop, hook it up to AC power and try with nothing attached.

If this does not work, and you can't get anything to spit out any text...... then you need to reinstall.

---

### Post by mörgæs on 2012-10-12
In case a proud gx150-owner googles the thread, this might help:
[http://ubuntuforums.org/showpost.php?p=12292664&postcount=828](http://ubuntuforums.org/showpost.php?p=12292664&postcount=828)

---

