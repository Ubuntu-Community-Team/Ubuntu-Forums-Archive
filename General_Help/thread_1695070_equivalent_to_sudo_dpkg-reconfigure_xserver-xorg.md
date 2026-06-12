---
title: "equivalent to sudo dpkg-reconfigure xserver-xorg"
date: 2011-02-25
forum: General Help
---

### Post by leppel on 2011-02-25
Hello everybody!
I recently became an owner of a really old school storage server, a compaq proliant 3000 server. In ubuntu 7.10 / 8 i was able to get the video to work. Now, after using the package manager and update, I upgraded my system to 10.10. 

The command to change settings for xserver changes from sudo dpkg-reconfigure xserver-xorg to sudo dpkg-reconfigure -phigh xserver-xorg. 

neither do the trick. When i try the dpkg with the -phigh one, i just get the prompt back. I have been told that they, for a lack of a better term, "decommissioned" this command. Does anyone know the equivalent command? I keep getting screen resolution too high when i boot, so i never even see the loading screen. When i hit escape and enter grub, i have like 6 recovery consoles, and whatever i enter will not stay after a reboot (for example, every time i reboot or enter a console, i have to bring up eth0 and eth1, as well as do mount -n -o remount /, because it puts /etc/fstab into read only.

I've been cracking at this for days, and could really use some help. I have tried editing xserver.conf and whatnot, with no results. 


PLEASE HELP!

---

### Post by dino99 on 2011-02-25
the actual kernel(s) directly deal with X, that means several things:
- all old commands are not required or dont work or break everything
- xorg.conf is not needed, and old one often push the mess higher

So, into a terminal, run:

sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Open synaptic (system admin synaptic) and remove/purge everything about installed grub packages
Then open nautilus and search "menu.lst", then delete them if any.
Back to synaptic, install grub-pc & grub-common

sudo update-grub

sudo shutdown now -R

sidenote: on single OS system, the grub menu is hidden by default, hold "shift" key down at end of bios process to see it

---

