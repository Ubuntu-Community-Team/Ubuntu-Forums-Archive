---
title: "X dying, system partially unresponsive"
date: 2009-09-10
forum: General Help
---

### Post by dal on 2009-09-10
Been having a weird issue with X on and off for some time now. Basically what happens is that both screens go blank, the system refuses to respond to the ctrl-alt-Fx terminal switching key combos and the only way I can get anything back on the screen is by resetting the machine. I can ssh in from another machine, but there is rarely anything in dmesg indicative of the system's current state, although once I did notice these entries:

[ 9144.681768] Xorg[4571]: segfault at 9643f000 ip b6426fbc sp bfe17d40 error 6 in nvidia_drv.so[b63b7000+3c5000]
[ 9173.636422] pidgin[5969]: segfault at 8f1c000 ip b7e8c253 sp b3ff4790 error 6 in libX11.so.6.2.0[b7e5d000+ea000]

Running sudo init 1 from the ssh terminal doesn't result in the machine becoming responsive again, I still need to reset.

This issue usually occurs when running World of Warcraft under wine, which lead me to believe that was the culprit, but I've just had it happen to me when all I had open was a dolphin window, firefox, pidgin and a couple of konsole windows. I had thought that the problem might be related to stressing the graphics card but just now I didn't even have compiz turned on so that is unlikely.

Generally when I ssh in after this issue occurs when World of Warcraft was running, top gives me the game process at very low cpu usage and X at very high usage (the reverse of what you usually see playing the game). SSHing in just now (after it crashed without WoW running), top showed everything at pretty much no cpu usage (0.1%us), and as mentioned the last thing in dmesg was unrelated (I think from memory it was when I plugged in an external hard drive, about half an hour before X died).

I've also tried the sysrq key combos with the machine in this state, and seen no results (the reboot combo had no effect, at least) other than that after I hard rebooted the system I found this in /var/log/kern.log:

Aug 29 09:46:57 k-desktop kernel: [ 4239.970359] SysRq : Keyboard mode set to system default
Aug 29 09:47:05 k-desktop kernel: [ 4247.586370] SysRq : Keyboard mode set to system default
Aug 29 09:47:14 k-desktop kernel: [ 4256.482374] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK aLlcpus showMem Nice powerOff showPc show-all
-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks

So on some level the system was still responding to keyboard input, just ignoring ctrl-alt-Fx, the reboot sysrq combo and anything else I typed.

My system is as follows:

Kubuntu 9.04, 2.6.28-15-generic kernel, xserver-common 2:1.6.0-0ubuntu14, xserver-xorg 1:7.4~5ubuntu18, nvidia 185.18.14 drivers on a 9600gt (although the same problem occured with two different driver versions from the 180.xx line, and an older one than that (although it's version number escapes me)).

Anyone come across a problem like this before?

Edit: the problem has occured under KDE, gnome and xfce, if that makes a difference.

---

