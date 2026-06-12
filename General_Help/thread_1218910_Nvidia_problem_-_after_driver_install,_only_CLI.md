---
title: "Nvidia problem - after driver install, only CLI"
date: 2009-07-21
forum: General Help
---

### Post by lenn-art on 2009-07-21
I recently upgraded from 8.04 to 9.04. My PC has 2 Nvidia cards and 3 monitors. For this multi-monitor setup, i need the nvidia drivers up and running so i can run nvidia-settings.

But i'm stuck on the first step, installing nvidia-drivers for my main screen. After installing i activate the legacydrivers from Nvidia (tried 180 and 173). But rebooting results in a CLI. I searched, googled and tried .. but nothing helps. It seems that the nvidia driver can't find the right monitor. How can i set this up?

------ edit: possible solution (works for me)
[LIST]
[*]Install ubuntu
[*]Install EnvyNG
[*]Install nvidia-settings (if it's not installed)
[*]Run EnvyNG to install Nvidia drivers
[*]Go to TT1 (Ctrl-Alt-F1 > caution! You leave the graphical environment. You have to write down these instructions)
[*]login
[*]stop the graphic shell by typing "sudo /etc/init.d/gdm stop"
[*]run sudo nvidia-xconfig
[*]start the graphic shell by typing "sudo /etc/init.d/gdm start"
[*]Go to TT7 (CTRL-ALT-F7)
[*]run from the CLI "sudo nvidia-settings" to configure monitors (don't forget to save)
[*]Backup the xorg.conf of course (maybe you need some extra tweaking in this).
[*]Now you can restart the PC.
[/LIST]

---

### Post by lenn-art on 2009-07-22
Solved. I put the solution in the startpost

---

