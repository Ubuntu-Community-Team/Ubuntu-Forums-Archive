---
title: "I need to repair grub from karmic live cd"
date: 2009-10-31
forum: General Help
---

### Post by JC Cheloven on 2009-10-31
Well, it have not take too long for me to mess up my shiny karmic install :-D

In short: yesterday I did a complete reorganization of one computer. I installed 64studio, then Karmic64, then UbuntuStudio Jaunty64. So the grub boot was in the last one. Then I decided to wipe that last one (why is a different story). 

I thought I would be able to repair the bootloader from live cd, as I used to: from the grub shell, running "root..." and "setup..." commands. But there is no grub console in the new version. Everything is different anyway.

Well I tried to find out in the info pages, and I guessed that i should run something like:
sudo grub-setup --directory=/media/ub-karmic64/boot/grub (hd0,5)
But it complains about a "syntax error near the unexpected '(' ", even though the command seems (to me) compliant with the scarce info manpages.

So I'm stuck. Any hints, please?

---

### Post by todak on 2009-10-31
See if [this]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") will help you. ;)

---

### Post by JC Cheloven on 2009-10-31
Thaks todak, that might be useful, but it's rocket science compared to the simplicity of the previous grub. I don't think I'll manage to learn by memory the process.

Anyway, I've follow the steps, grub has installed,_ but there is only a boot entry for karmic._ My old xp (which I didn't use in ages, but anyway), has been ignored (WTF??).

My hope was to devote this saturday to audio/music stuff in linux, not having the day spent in fixing a boot thingie. Now installing jaunty64 on some spare disk space, for the sole purpose of controlling the boot process. I suposse I could install grub from jaunty live, but I'm not feeling like editing UUID's and the like ... 

OH, look, it has just finished, while I wrote this... let's see ...yes, there are all entries ...  SOLVED.  (not marking it as such, obviously).

---

