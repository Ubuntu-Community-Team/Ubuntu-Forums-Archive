---
title: "Error No Such Device,Grub Rescue"
date: 2011-04-07
forum: General Help
---

### Post by paulmckey on 2011-04-07
Hello! I have a Lenovo ideapad s10e with 4 HDs to it. I have windows xp as first OS,ubuntu 10.04 as other.

Here's the situation:
I installed Ubuntu 10.04 using Wubi.I can dual-boot,no problem at all.
After I logged in to Ubuntu,i downloaded a set of updates. The next day,there's a prompt for an ubuntu update (10.10?). So i installed the update for an hour or so,then a menu for this "grub" appeared. So I just clicked it.

After the update has been finished and my laptop rebooted,I cannot boot,instead this option appeared:
ERROR NO SUCH DEVICE (some sort of numbers)
GRUB RESCUE>

I saw some solutions but none worked for me so far. I tried restoring my windows xp bootloader using a recovery pack but it doesn't load. I also tried supergrub2 and it doesn't load,too (I used usb.)

Anyone can help me? I'm new to linux. I don't want the hassle of fix my laptop :(

---

### Post by bcbc on 2011-04-08
You just need to install the windows bootloader. Boot from the Windows DVD to a repair prompt and run: fixmbr

See the wubi megathread for details: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

