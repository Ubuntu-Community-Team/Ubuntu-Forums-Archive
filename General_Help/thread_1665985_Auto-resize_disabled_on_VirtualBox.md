---
title: "Auto-resize disabled on VirtualBox"
date: 2011-01-13
forum: General Help
---

### Post by jackbuntu2011 on 2011-01-13
I've installed Ubuntu 10.10 on my VirtualBox 4.0.0 on Windows 7 64bit. 
At first I only had 2 resolution options: 600x400 and 800x600. After installing Guest Additions I also got an option for 1024x768. 
But my resolution is 1920x1080. In VirtualBox Machine->Switch to seamless mode and Machine->Auto-resize Guest Display are disabled. 

I've read on other topics, that installing a newer version of VirtualBox could solve this, but I believe I already have the latest. 
Also there were suggestions on changing xorg.conf file to use VirtualBox drivers, but I don't even have this file. And when I created the file and copied default-ish configuration, then the OS wouldn't boot the desktop environment. 

I have 2 monitors hooked up, but I don't see how this could be the problem.

Any ideas?


EDIT: Solved it. 
Originally I ran VBoxLinuxAdditions.run from the Guest Additions, but what I should have ran was autorun.sh.

---

