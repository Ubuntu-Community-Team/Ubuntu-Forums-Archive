---
title: "Ubuntu 12.04 32bit, TOTAL freeze right after desktop"
date: 2012-05-16
forum: General Help
---

### Post by julian90 on 2012-05-16
Hello,

I recently bought a new acer laptop, I installed windows 7 64 bits and then I installed ubuntu 12.04 32 bits.

I all my drivers were succesfully installed, I didnt activate my radeon graphics drivers though because previously they had messed up the GRUB (booting).

Now here is the problem.  Whenever I turn on my laptop after a while of inactivity and I select my ubuntu OS on the boot screen, ubuntu runs okay until the desktop is displayed on screen, I can move my mouse cursor for 3 seconds or so before the system COMPLETELY freezes.  I have tried all keyboard commands and they do not work, everything freezes, so im forced to turn off my laptop.

And here is a clue to whats going on. If I restart my computer while using windows 7, and then go into ubuntu, everything works perfectly until i turn off my laptop again.

Thanks for your help.

---

### Post by julian90 on 2012-06-03
I discovered the problem is the wireless internet application.  When it loads the system completely freezes.  Unless I just used windows, weird I know, but thats what happens...

---

### Post by cgsimtech on 2012-06-07
I've got the same problem. I think you're right about the wireless driver.
When booting normally, my desktop freezes right after logging in.
When booting in "safe-mode", the system boots up fine except I have no wireless connection.
I then powered down my laptop and turned the wireless switch to off. Then, I powered up and rebooted in normal mode. The system came up normally but of course the wireless was trying to connect to my router but couldn't because I had the switch in the off position.  So, I turned the wireless switch "on" and my wireless connected to my router.
However, the Internet connection was slow as molasses.
So, the key in my observation is the wireless driver.  For now, I'm using a wired connection to a wireless access point until this issue is resolved...

Laptop: Toshiba Satellite M45-S169
Wireless driver: ATH5K
OS: Dual boot w/ WindowsXP and Ubuntu 12.04 on seperate partitions (ext4/swap)

---

