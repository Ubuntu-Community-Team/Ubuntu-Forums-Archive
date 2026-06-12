---
title: "Cannot start GRUB after Standby &amp; Restart"
date: 2010-12-24
forum: General Help
---

### Post by FalleStar on 2010-12-24
My laptop (ASUS K72DR) is running Ubuntu 11.04 x64 and Windows 7 Professional x64.

Everything seems to work just fine under Linux, except for resuming after standby. I can shutdown and restart the machine as many times as I want and there is no problem when doing so. The laptop goes into standby just fine, and comes out of it just fine. HOWEVER, upon shutting down or restarting the laptop any time after I have gone into standby, I am presented with a black screen and a flashing "_" in the top-left corner of the screen where GRUB would normally display the list of available operating systems to boot.

Strangely, I have found that booting into GParted Live off of a USB flash-drive works as a temporary fix. The unusual thing is that I don't have to do ANYTHING within GParted Live, I simply boot into it and then restart it immediately. After the machine is restarted I am presented with my normal GRUB menu.

This problem occurs on a fresh install, I've tried re-installing the OS and GRUB several times in the past with the same problem each time. I can manage to get by for now using the Windows 7 partition or by just shutting down the laptop instead of putting it to sleep on Linux; however, I'd like a more permanent solution as this is not acceptable in the long run.

---

### Post by RRMX on 2011-06-13
Hello,

I have the same laptop and the same problem (with Debian). However your message gave me the reason why this was happening. I have not found a proper solution yet; however, instead of booting on your memory stick, you can as well take off the battery, put it back on and turn the computer on; it'll work.

I hope someone finds a solution as well

---

### Post by FormatSeize on 2011-06-13
> **RRMX said:**
> I have not found a proper solution yet; however, instead of booting on your memory stick, you can as well take off the battery, put it back on and turn the computer on; it'll work.
 
I hope someone finds a solution as well
Back when I had a laptop, I had this same issue, and this is what I would always have to do if I left the computer unattended.

---

### Post by Phil Stone on 2011-06-13
RRMX,

this thread also shows that this is a problem encountered by long term users of linux. [http://ubuntuforums.org/showthread.php?t=1460014&highlight=suspend+option+shutdown+menu](http://ubuntuforums.org/showthread.php?t=1460014&highlight=suspend+option+shutdown+menu)

Removing and replacing hardware such as the battery for such issues is not the best solution. Until a solution is resolved/implemented you are better to disregard the suspend option. Linux shuts down and boots quite quickly in my experience. While this may be an annoyance it is better than mistreating the hardware. If preferable you could also ensure a swap partition is available to linux and use the hibernate option as this may be a faster solution than shutting down.

Hope you find an answer.
Phil

---

