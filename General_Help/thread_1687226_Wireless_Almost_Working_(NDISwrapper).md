---
title: "Wireless Almost Working (NDISwrapper)"
date: 2011-02-13
forum: General Help
---

### Post by Tarkan640 on 2011-02-13
I am trying to set up wireless on my desktop. I would have to move my whole computer to get ethernet, so it completely has no internet. I have my laptop here next to it. I have a microsoft mn710 wireless adapter/card (what is it called) via USB in the desktop and of course, ubuntu does not recognize it. I installed ndiswrapper (although I am not sure how successfully) and supposedly wrapped the driver mn710.inf along with its required files.

ndiswrapper -l
returns driver installed and device present.

I do not know how to get it working now. The command:
sudo modprobe ndiswrapper
returns:
"FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernal/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory"

Is "modprobe ndiswrapper" supposed to make the wireless work?
I have already typed ndiswrapper -m and also added the ndiswrapper to the modules file thing that loads on boot.
I've restarted the computer several times and the wireless device remains without lights.
Could anyone help me please?

---

