---
title: "Best setup to wirelessly control my desktop?"
date: 2012-10-08
forum: General Help
---

### Post by Stonecold1995 on 2012-10-08
I'm planning on setting up my XPS desktop so I can control it wirelessly, but I'm not sure the best way to go about doing it.  I need to have Windows on it so I can run Folding@home, but I'm probably won't be in physical proximity of the computer for a while, so I need a way to monitor and control the system through SSH.  I am much more familiar with GNU's commands than Windows' commands, so if possible I'd like to be able to control it using commands I am familiar with.  I need basic functionality like:
- Modify, create, delete files and directories
- Start and kill process
- Install and remove software
- Change system settings, directly through the Registry if necessary

My current ideas are CygWin, or VirtualBox.  If I use CygWin, will it be able to do all of this, like Wine's Command Prompt, or will it be more like DOSBox where it's isolated from the rest of the OS and it can't really interact with it?  If I use VirtualBox (Windows host, with either an Ubuntu or maybe Debian guest), will it be possible/safe to control Windows with it through shared folders?

So what's the best way to go about controlling Windows with Ubuntu?

---

### Post by HiImTye on 2012-10-09
you can use F@H on Ubuntu
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by Stonecold1995 on 2012-10-09
I need to be able to do GPU folding, and the Linux version doesn't support that.

---

