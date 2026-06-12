---
title: "Boot-up periodically fails"
date: 2010-08-04
forum: General Help
---

### Post by CanolaOil on 2010-08-04
Hey everyone,

I've got ubuntu(10.04.1 LTS) dual-booting with Windows 7 on a Dell Studio laptop. Earlier, I had to do a lot of tom-foolery to get the dual-boot to work right since something in Dell's software or Windows software would nuke Grub, and leave my computer unable to boot into any OS. To fix that, I had to switch from Grub 2 to Grub 1, and then from my understanding cause Grub 1 to run later in the boot-cycle(I think I either caused to skip stage 1.5 or else start from there..or something..I'm new to all this :P).

So anywho, things are generally working pretty good, except now when I boot into Ubuntu it randomly fails to start. I'll choose Ubuntu from Grub, then it will print out the text "Boot from <some boot info>. Starting up..." and then hang and never go. But this happens intermittently.

So _something_ is failing at boot-up, I just have no idea how to check/enable the logs/where they are. I tried using this: [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925) but I think that has no "history" for those bootlogs + I couldn't get it to work anyways.

Thanks!

CanolaOil

---

