---
title: "computer crashing"
date: 2010-07-11
forum: General Help
---

### Post by tommah04 on 2010-07-11
hi all,

I dual-boot Windows 7 and Ubuntu Koala amd64.  Recently my Windows started crashing during startup (no blue-screen, just freezes) but ubuntu still worked.  Eventually I tried just completely reinstalling Windows 7 but during installation it just crashes so its impossible to re-install windows.  Then I tried wiping the hard drive clean then installing windows, but its still crashing during installation.  Then tried re-install Ubuntu, and now that's crashing during installation.  

At first I thought it might just be over-heating being summer an' all, so I threw a fan on it and left it alone for a while to cool off,  but now its stilling crashing and I can't do anything with my computer.

any ideas?

---

### Post by cj.surrusco on 2010-07-11
During what part of the installation is it crashing? Are you able to boot into the live CD? You could try checking the disk if you are able to get into the live CD, because it sounds like a hard drive error to me.

---

### Post by tommah04 on 2010-07-11
it crashes at all different times, but I guess it crashes MOSTLY during the actual installation part.  

it DOES work fine under LiveCD.  so its a Hard drive error?... should I just junk this and buy a new one, or is there a fix?

---

### Post by mike555 on 2010-07-11
I just fixed a Windows computer that was crashing all the time ..... it was badly fragmented , so bad that the builtin defrag would not work, I had to use a portable defrag program on USB stick , two hours later it now works good ....  so you might try that.

---

### Post by tommah04 on 2010-07-11
well that's the thing, I just completely wiped the hard drive clean so I wouldn't think it'd be a problem, would it?

---

### Post by cj.surrusco on 2010-07-11
I would try booting into a Live CD and using fsck to check the file system that you put on there. The fsck manual can be found [here]("http://manpages.ubuntu.com/manpages/jaunty/man8/fsck.8.html").

---

### Post by tommah04 on 2010-07-11
I wiped the hard drive so there isn't any linux file systems on there anymore and I can't even install one because of the crashing

---

### Post by cj.surrusco on 2010-07-11
Try using the Disk Utility (under **System>Administration**) to check the disk.

---

### Post by mike555 on 2010-07-11
If you can boot a live cd , you might try a harddrive test cd ... there are free ones out there .

---

