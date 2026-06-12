---
title: "Problem with keys Tab, Caps, Shift, Ctrl, Alt, Super stop working."
date: 2010-10-16
forum: General Help
---

### Post by Kalidarn on 2010-10-16
Hi,

I'm running Kubuntu 10.10, with KDE 4.5.2, what I've noticed is every so often my Tab, Caps, Shift, Ctrl, Alt, Super keys stop working. I'd been running Ubuntu 10.04 with Gnome and hadn't ever come across this issue. I'm not sure if this is related to KDE 4.5.2 or is possibly because I updated to 10.10 and would also occur on a Gnome environment.

If I switch to my virtual machine (VMWare Workstation 7.1.2 build-301548 which I was able to get working on 10.10 using [http://ubuntuforums.org/showthread.php?p=9975416](http://ubuntuforums.org/showthread.php?p=9975416) ) the keys work within that but if I switch back to my host desktop they stop working.

To fix it I've found logging out or unplugging the keyboard and plugging it into a different USB port fixes it.

I did find this thread: [https://bbs.archlinux.org/viewtopic.php?id=45359](https://bbs.archlinux.org/viewtopic.php?id=45359) however I'm not sure if it's related.

I'm wondering where the best place to look for a solution to this problem might be.

Edit: This is a VMWare bug by the looks of it. [https://lists.ubuntu.com/archives/kernel-bugs/2008-August/039652.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-August/039652.html) [https://bugs.launchpad.net/bugs/195982](https://bugs.launchpad.net/bugs/195982)

> TEST CASE:
1. Click inside the VM and
2. Hold any of the Ctrl, Alt and/or shift keys while releasing the keyboard/mouse to the host OS (which you obviously do when you press Crtl-Alt to revert back to windowed mode, as the cursor is then released from the VM).

WORKAROUND:
After this happens to recover your keyboard execute 'setxkbmap' in a terminal

As I'm using one of those [Apple Aluminium Keyboard](https://help.ubuntu.com/community/AppleKeyboard) ```
setxkbmap -verbose 10 -model pc105
``` seems to do the trick.

---

### Post by T.Ephraim on 2010-11-25
Thx a lot! I had that bug too and calling setxkbmap without any parameter fixed it here.

Ciao Ephraim

---

