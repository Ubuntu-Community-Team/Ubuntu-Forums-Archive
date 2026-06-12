---
title: "Nvidia Proprietary drivers do not work after fixing ugly text only bootscreen."
date: 2011-09-25
forum: General Help
---

### Post by Trymos on 2011-09-25
When i did a fix to fix the ugly text only boot screen i logged in and i logged into gnome and not unity.

I went to additional drivers and clicked my driver and it says "This driver is activated but not currently in use"

What is happening? Please help me. If you guys need any additional info just let me know.

---

### Post by .... on 2011-09-25
Are you having issues? If not, then don't worry about it. It's an annoying (but benign) bug that it shows as not in use when it really is: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---

### Post by Trymos on 2011-09-26
> **.... said:**
> Are you having issues? If not, then don't worry about it. It's an annoying (but benign) bug that it shows as not in use when it really is: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)
This is a bug that makes my bootup screen look like garbage at the very end. This is usually only caused to me when no graphic drivers are in use.

Plus the fact that it just instantly boots into gnome when i select unity.

---

### Post by Trymos on 2011-09-27
Sorry for bumping this, but i need help!

Just wondering, in startup manager will 800x600 startup resolution fix my driver problem? I set it to 1024x768 and it just started doing this.

---

### Post by JovialJaybird on 2011-09-27
I too am having the same issues (ugly boot screen, and driver activated but not is use) but I didn't "fix" my boot screen like 'Trymos' did.
 
This happened from when I first installed 11.04.  With the driver in place but "not active", the highest resolution I am allowed to choose from is 680x480 (booting live from the cd I had it set at  1900X1200).  If I deactivate the driver, it will allow me to go up to 1024x768, but that's hardly acceptable.
 
Reinstalling Nvidia drivers didn't help whatsoever.

---

### Post by realzippy on 2011-09-27
> **JovialJaybird said:**
> I too am having the same issues (ugly boot screen, and driver activated but not is use) but I didn't "fix" my boot screen like 'Trymos' did.
 
This happened from when I first installed 11.04.  With the driver in place but "not active", the highest resolution I am allowed to choose from is 680x480 (booting live from the cd I had it set at  1900X1200).  If I deactivate the driver, it will allow me to go up to 1024x768, but that's hardly acceptable.
 
Reinstalling Nvidia drivers didn't help whatsoever.

Maybe you start an own thread,problems are not related.

---

### Post by Trymos on 2011-09-27
I managed to temporary fix the problem by reverting to the text only boot screen.
I also did not mention that the text only boot screen just started happening when i made it appear quickly by adding the line to the conf.d/splash file: FRAMEBUFFER=y

---

### Post by JovialJaybird on 2011-09-27
Yes, thank you.  Sorry to bother you.

---

