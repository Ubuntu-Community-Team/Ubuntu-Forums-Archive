---
title: "Windows boot loader and Grub, how to switch?"
date: 2011-07-09
forum: General Help
---

### Post by aerial_001 on 2011-07-09
I want to be able to switch between the two operating systems while connecting remotely. But how?

Here's the situation:

I installed Ubuntu with the windows installer: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

I have windows 7. Now when I restart the computer, I see windows boot loader first which gives me the options: Windows 7 or Ubuntu. If I choose Ubuntu, I see the Grub 2 menu, and I can select between Ubuntu and Windows. 

If I'm in windows, I can change the boot to Ubuntu, and restart the computer remotely, and when it comes back up, Ubuntu is running. No problem so far.

But, if I'm running Ubuntu, I can only modify Grub list. After restart, windows boot loader comes up (which is set to ubuntu), then Grub comes up (set to Windows now), but Grub sends me back to Windows boot loader, and there's an endless loop. 

So I really dont know how to switch to windows remotely. I think if I can modify windows boot loader through ubuntu, then everything should work, but I didnt find anything googling.
Also if I can find a way to modify Grub through Windows, and if somehow I can remove the Windows boot loader then that should work also, but I dont know how to access Grub from Windows, and how to remove Win boot loader without messing with everything else.

Help or suggestions would be appreciated.

---

