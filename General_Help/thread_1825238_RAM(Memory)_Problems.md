---
title: "RAM(Memory) Problems"
date: 2011-08-15
forum: General Help
---

### Post by M1ttenz11 on 2011-08-15
Alright, sometimes when I turn my computer on I might get Busy box error or some INITRAMFS and sometimes even after playing a game through Wine,(Usually only happens through wine if wine has some like fatal error.) so I take my RAM out and back in and everything is fine. So I came up with INITRAMFS = Initial, RAM Failures, not sure if its correct, just wondering if some one could shine a little light on this problem that I have, and could direct me to some form of solution to stop this from happening or just to confirm that one day I wont melt my computer due to this error.
Also, the odd time here and there I have had Busybox error and taking ram out and re-inserting isn't the solution, re-installing grub is - via live cd. [sudo apt-get install grub]typing this in terminal has been a solution at certain times, but why does Grub or my RAM get failures? or could it just be that one of my cards or slots could be faulty, or on its way out if you get me?

Thanks :b.

---

### Post by mcduck on 2011-08-15
Initramfs is not an error message for RAM failure, it's short for "Initital RAM Filesystem". When Linux is booting it loads the kernel into Memory together with a small temporary filesystem to get some space to work with until it gets all the actual filesystems mounted.

What exactly is the problem, and how to solve it, depends on the *exact* error message you get. So next time you see it, type it down and attach here.

Without seeing the exact error, my guess would be some kind of hardware problem, most likely related to your hard drive and the way it's detected.

Still, if you want to check the RAM anyway, there's the memtest option in the Grub menu and on the Live-CD. Let it run several times through, at least over night, and if you get no errors you can be sure your RAM is working fine.

---

### Post by M1ttenz11 on 2011-08-15
Got you, Initial RAM file system ;)
My guess was more along on the idea on how to remember to fix, but thanks I will try the memory test and when I get to my girlfriends I will write down the error code because I have that there,
I will more than gladly take your word for it, as it being a hard drive problem, I just hope it can be sorted out.
ITS NOT DEADLY VITAL, the computer does work, just I'd prefer to see less of this error message, and my mam probably would too ha :)

Error Code -
[SOMETIMES] [B]no init found, try passing init = bootarg. busy box U1.13.3(Ubuntu  1:1.13.3-1 ubuntu11) built-in shell (ASH) Enter 'help' for a list of  commands. (init ramfs) [1.067073] usb 2-1:configuration #1 choesen from 1  choice
[/B][AND OTHERS]
[B]no init found, try passing init = bootarg. busy box U1.13.3(Ubuntu  1:1.13.3-1 ubuntu11) built-in shell (ASH) Enter 'help' for a list of  commands.
[/B]
Exact same as the other, just with out the extra bit so i was curious if that actually makes a difference or not so i thought i would list that just incase its actually two different problems.

---

