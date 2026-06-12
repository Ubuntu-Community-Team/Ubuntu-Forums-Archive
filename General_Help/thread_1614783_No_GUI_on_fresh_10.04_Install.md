---
title: "No GUI on fresh 10.04 Install"
date: 2010-11-06
forum: General Help
---

### Post by CoreyJKelly on 2010-11-06
Hi all,

I just performed my first (successful?) Ubuntu installation. The installation process seemed to go fine, and I selected "Ubuntu Desktop" when asked which set of packages I wanted to install. I assumed this was a standard choice.
After the installation finished, the system rebooted and brought me to a login prompt. I'll mention at this point that I have SOME prior experience with Linux systems, but I'm by no means an expert, and I'm new to Ubuntu. I logged in and tried startx, only to be informed that it was not installed. Having performed a network install, I have internet access on the machine, so I tried "sudo apt-get install xinit" which seemed to work, but now when I run startx, my window shrinks to a portion of my monitor size, the colours invert (black prompt on a white background) and the system locks up. 
I'm assuming this is some sort of video driver issue, and could probably explore further, but I figured I'd ask some experts first.

Any advice would be greatly appreciated!

---

### Post by CoreyJKelly on 2010-11-06
Oops, I forgot to mention, I also tried 

sudo dpkg-reconfigure xserver-xorg

which didn't seem to do anything (no output to prompt.)

---

### Post by CoreyJKelly on 2010-11-06
Alright. Sorted this one out myself, and I feel kinda dumb. It didn't seem sensible to me that X wouldn't be included in the "Ubuntu Desktop" setup, so I went ahead and re-installed (didn't have anything to lose, and wanted to go for 10.10 anyway)
Realized this time through the installation process that I had to hit space to select the desktop installation, then enter to confirm. Last time I just hit enter and proceeded to install the Ubuntu core. I'm up and running now, so I'll surely be back around with more difficult questions soon.

---

