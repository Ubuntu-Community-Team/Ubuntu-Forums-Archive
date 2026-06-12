---
title: "split screen after boot - user's log in"
date: 2012-01-25
forum: General Help
---

### Post by robergeb on 2012-01-25
Hi everyone,

I downloaded Ubuntu 11.10 last night and created a boot DVD (32 bits edition). The installation worked fine and I was asked to reboot at the end. However, when I arrived at the log in screen, I noticed that my screen was separated in half; click on the link to see the picture: [https://plus.google.com/u/0/112916713984257628048/posts/d1pAFWJpwHi](https://plus.google.com/u/0/112916713984257628048/posts/d1pAFWJpwHi). The picture is a screenshot from Linux Mint 12, but I have the exact same problem on Ubuntu. The weird thing is that I can still enter my password. However, after I hit 'enter', the screen remains separated in half and I can't access the menus, the applications, nor the right click function. Even if I reboot, I still have the same problem.

I also downloaded, burned, and installed Linux mint 12. Same problem.

For your information:

I didn't installed Linux alongside windows. It was a format and full install. I'm using a desktop PC at the moment. As for my hardware, my graphic card is a Radeon HD 7xxx Serie. Intel motherboard and 6 gb of RAM, DDR3, Corsair. My HD is a Western Digital, 1tb. My screen is a ViewSonic 27''.

Thank you for your help!
Benoit

---

### Post by robergeb on 2012-01-25
I think I might have found something..some users experiencing the same issue with Ubuntu.

The code below should fix the bug. I will try that tonight and update this thread accordingly.

sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

---

### Post by robergeb on 2012-01-26
Last night I created a bootable USB key. I formatted and re installed Ubuntu 11.10. Everything works fine now! Maybe there was something wrong with my Linux dvds. However, the sudo commands I pasted above are also working if you have an issue with the ATI Radeon HD cards.

Solved!

---

