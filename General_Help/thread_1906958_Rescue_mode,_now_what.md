---
title: "Rescue mode, now what?"
date: 2012-01-10
forum: General Help
---

### Post by MyD0j0 on 2012-01-10
I'm having some boot problems.  I've been using ubuntu for a while, but this is the first time I've had boot problems so now that I have a shell prompt, I'm not sure what I need to do to analyze what I need to do next.

Part of the problem is when I use the command line ('dmesg' or 'ls -al', for example) the output goes by so fast and I haven't figured out how to pause it...

Any pointers on what I should do next?

Thanks!

---

### Post by Bucky Ball on 2012-01-10
Have you tried 'startx'? What message do you get. You don't mention the release you are using.

---

### Post by QIII on 2012-01-10
It might be helpful for you to better describe "boot problems".

---

### Post by searchfgold6789 on 2012-01-10
What you do next depends on exactly what problem you're having, because different shell commands do different things ;)

---

### Post by raja.genupula on 2012-01-10
use this link 

[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

---

### Post by MyD0j0 on 2012-01-11
> **QIII said:**
> It might be helpful for you to better describe "boot problems".


Sorry folks...I knew better than to leave an obscure post asking for help and I have no excuse; thanks for replying in an attempt to help despite my failings...

Hardware, system and other details on the problem can be found at this post: [http://ubuntuforums.org/showthread.php?t=1905478](http://ubuntuforums.org/showthread.php?t=1905478)

(I also realize I shouldn't cross post like this, but after that post got 143 views and the only replies were my own, I figured I posted in the wrong place or something.)

I appreciate the assistance, I really do!

---

### Post by MyD0j0 on 2012-01-11
> **Bucky Ball said:**
> Have you tried 'startx'? What message do you get. You don't mention the release you are using.

The system is mounting read only so I get a lock error.

---

### Post by MyD0j0 on 2012-01-11
Not sure what I did to finally get the system to read/write, but when it did, I used the xorg.conf.backup to restore and was able to get the system back up normal.

---

