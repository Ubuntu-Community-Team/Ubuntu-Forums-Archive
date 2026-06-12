---
title: "I screwd up my X11 Conf file :D"
date: 2010-08-22
forum: General Help
---

### Post by cyberyder on 2010-08-22
Hi everyone!

I've been using ubuntu for at least one year or so, enough to understand some parts of it :)

I've got a special set up: a dual svi nvidia videocard that allows me to use two screen with their wonderful twinview. (i know not that surprising everyone does dual monitor anyway)

so i decided to go and bring my box darling to my IRL darling (aka girlfriend) and work there for the whole week.  Knowing that there might be some room issue, i only brought one monitor and wisely though that i should set my desktop to only one monitor before moving there....

So i used the crappy nvidia editor (that you have to start from the command line using sudo.....LOL) and removed the second screen. restarted the session and there screen went avock. therefore rebooting the computer. Now it gets stuck at the " "ubuntu" with five red dots under " loading screen.  

i'Ve waited for 10 minutes and nothing came on. even tried to press esc to know where the process was and could find anything. 

I've got two idea of solution
1 - use command line to restore the backup x11 conf file i've done before playing with the nvidia thing (wise heh?)
2 - use command line to tyoe in what i actually want to set up for my monitor (i guess i can figure this one out by using on forum and stuff)

both imply that i need to play with the command line and i dont know how to get there. when booted my computer directly goes into the GUI and then fail. :(

do you have any other idea or do you know how to get to the command line without going to the gui?

please dont TLDR my wall of text :P

my set up
ubuntu 10.04 64 bits
inter i5 650
4gig ram
nvidia Gforce Gtx 260

---

### Post by bergfly on 2010-08-22
I'd try step one first, as long as you have a backup of X11.conf that you know is good you should be golden. 

Two  quick ideas. Firstly, if the boot gets far enough along, Ctrl-Atl-F2 should give you a terminal.

Secondly, you could try booting from a live CD/USB and replacing the new X11.conf with the old once you have access to the drive.

---

### Post by Brandon Williams on 2010-08-22
Is your system configured to show you a grub boot menu? It sounds like the answer is no. You should still be able to get to the boot menu by holding down the shift key when you boot. If that doesn't work, try pressing the escape key repeatedly on boot. When you see the menu, use it to boot into recovery mode, which will give you console access as root.

If you just can't get to the boot menu, then boot with a live CD and use it to fix the config on your disk.

For future reference, X should be able to handle almost any single-monitor setup without the use of an xorg.conf file. In my experience, it will handle most dual-monitor setups without an xorg.conf file, too. Try just renaming or removing /etc/X11/xorg.conf and allowing X to use its default config settings. You may need to run the 'System -> Hardware Drivers' config to enable the binary nvidia driver, but other than that, at least the single-monitor config should work just fine.

---

