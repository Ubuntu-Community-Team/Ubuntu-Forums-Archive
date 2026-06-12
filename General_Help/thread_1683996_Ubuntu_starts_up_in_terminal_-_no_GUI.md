---
title: "Ubuntu starts up in terminal - no GUI"
date: 2011-02-08
forum: General Help
---

### Post by SeanOK on 2011-02-08
Hi,

I'm new to Linux, and have just installed Ubuntu on my laptop alongside the existing Windows 7 installation, to try it out.

The problem is that Ubuntu will only boot into a terminal, asking for my username and password. Googling this problem seems to indicate that it may be a problem with graphics drivers.

I've tried commands such as "sudo dpkg-reconfigure -phigh xserver-xorg" and "startx" which I found through googling the problem, but neither of these did any good. I also tried reinstalling Ubuntu, but the problem didn't go away.

I can still boot into Windows so it's not the end of the world, but I'd like to get Ubuntu working. Any ideas?

Thanks :)

My system:
OS: Ubuntu 10.10 32-bit and Windows 7 Professional 64-bit
CPU: Intel P6100 2GHz
RAM: 3GB DDR3
Hard drive: 500GB, 30GB partition for Ubuntu, rest for Windows
Graphics: Intel HD Graphics

---

### Post by SeanOK on 2011-02-08
To clarify:

If I type "startx", the screen goes blank and nothing happens, and I have to restart.

---

### Post by sanderd17 on 2011-02-08
Does it work with the live CD?

---

### Post by Mad dog on 2011-02-08
What type of videocard are you using?

---

### Post by SeanOK on 2011-02-08
Thanks for the replies.

It does not seem to work with the live CD, the Ubuntu installation goes fine, however if I choose the option to try Ubuntu, it spends forever with a spinning mouse cursor and nothing happens.

As for the graphics, I'm not entirely sure, it just says "Intel HD Graphics" (I'm using Windows' dxdiag tool here). I think it's some form of integrated graphics.

---

### Post by SeanOK on 2011-02-08
Fixed! :D

The solution I found was to choose to boot into the recovery mode from the boot loader, from there I chose the dpkg tool, which updated a bunch of things including something intel (the computer's graphics chip) related. Once this was updated, I rebooted and it loaded the GUI without any problems.

Also note that I did try running the update from the terminal mode that it booted into in place of the GUI, but it never managed to complete because after some time, I believe it was attempting to load the GUI and failing.

But it's all good now, if anyone else has this issue, try the recovery mode and the dpkg tool.

---

