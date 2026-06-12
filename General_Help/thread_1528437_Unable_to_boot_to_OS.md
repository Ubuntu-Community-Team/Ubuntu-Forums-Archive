---
title: "Unable to boot to O/S"
date: 2010-07-10
forum: General Help
---

### Post by moindn on 2010-07-10
I installed Ubuntu 10, deleted my windows O/S, updated and rebooted with everything working fine. When I shut down completely and start the computer again, I get a "Minimal BASH-like line editing is supported". I then get a grub> and nothing further.
I have done this 3 times and get the same results. 
I would appreciate some direction. Do I have a computer problem or is there a work-around to get the system to boot?

---

### Post by drs305 on 2010-07-10
moindn,

Welcome to Ubuntu and the Ubuntu forums.  :-)

Since you aren't getting a "grub-rescue" prompt, Grub 2 probably can't find its files in /boot/grub of the drive it thinks they are installed on.

You can refer to the Ubuntu community doc's section on booting from the command line if you want to try to troubleshoot it for yourself:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

An easier path would be to run this "boot info script" and post the result between [noparse]```

```[/noparse] tags, which you generate by pressing the **#** icon in the post's menu. Here is the script link:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

