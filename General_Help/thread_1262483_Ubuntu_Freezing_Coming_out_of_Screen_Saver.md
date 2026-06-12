---
title: "Ubuntu Freezing Coming out of Screen Saver"
date: 2009-09-09
forum: General Help
---

### Post by blindape on 2009-09-09
Hi I'm Runing Ubuntu 8.10 on an Acer Laptop using a Wubi install.  Most things run great and I'm really happy with it but I have been having a re-curring problem for a little while now.

Every so often when the computer is waking up from sleep mode, screen saver or from lock screen it will either re-set/re-boot itself or it will freeze completely and I can't find any way of resetting things apart from shutting down the computer with the power button.  This manual shutting down of the computer has already once corrupted my boot files once which I have had to restore after running chkdsk in MSDOS.  

One other thing or symptom that has been happening from time to time in conjunction with this freezing is that every now and again when I shut down the computer properly it says that the power manager is not responding and I can choose to exit anyway or cancel the shut down process.

I am grateful for any help provided.

Regards,

John Curwood

---

### Post by lunarmelody on 2009-09-10
I'm having a similar problem.  I haven't found a solution yet, but try restarting in this case by holding down ALT + PRINTSCREEN and pressing r s e i n u b.  This should reboot the computer safely without corrupting boot files.

---

### Post by blindape on 2009-09-11
Hi lunarmelody, thanks for your reply

I this morning the computer froze again, all I had on the screen was the background wallpaper and the mouse pointer (which I could move by the way).  But there was no Icons and No Panels.  I tried holding down alt+PrtSC and then pressing r s e i n u b.
After reading your post I did some research and found in the ubuntu docs site a section on how to reboot cleanly when the mouse and keyboard are frozen, however none of the key combinations did anything at all.:(
I found this supprising and frustrating, especially since I was able to move the mouse pointer around the screen so I didn't think the computer could be That frozen.

Regards,

John Curwood

---

### Post by patmalcolm91 on 2009-09-29
I'm also having this exact problem. I get a hard freeze when waking up from the screensaver after an extended period of time. Neither Ctrl+Alt+Backspace nor the Alt+SysRq key combos work, and I'm forced to power down by holding the computer's power button (which has resulted in filesystem corruption once)

I found this thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/367464]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/367464") which I believe to be related to my problem, and down in the comments, someone mentions installing the 2.6.30 kernel.

I haven't yet attempted or tested this, but you may want to give it a try. I'll try to remember to post back here once I try it.

Patrick

---

### Post by RogerDavis on 2009-10-25
I'm also having this problem with the screen saver after a long time.  I haven't tried this, and it is probably the same as a full shutdown, but you might try the computer reset button instead of just pulling the plug.

Please post your result if you do try it.

---

