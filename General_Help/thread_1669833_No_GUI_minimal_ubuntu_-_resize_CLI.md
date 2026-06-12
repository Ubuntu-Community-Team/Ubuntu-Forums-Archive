---
title: "No GUI minimal ubuntu - resize CLI"
date: 2011-01-18
forum: General Help
---

### Post by vascop on 2011-01-18
Hi. I've installed the latest ubuntu minimal CD with the option "Command line install".

Ubuntu is installed. I'm running it on Virtualbox 3.2.12 (I believe its the lastest version). Setup is HOST: Windows 7, GUEST: Minimal Ubuntu (or whatever you call it)

Now my resolution is not maxed or at least good enough. I would like it to be at least 1024x768 (my monitor is 1366x768 max)

I tried to 
```
nano /boot/grub/menu.lst
```
but the file doesn't exist so I get an empty file. I read that I was supposed to go there and change a vga setting.

I do not have a GUI installed. I've been running ubuntu with a GUI for a while and decided it's time to move on. I also do not have xorg or any of that stuff (do I need it just to resize a console?)

Any help would be great

---

### Post by lithopsian on 2011-01-18
That file is for the old version of Grub.  You will be using Grub 2.  The relevant file for you  is called grub.cfg and there is a setting called gfxmode for the resolution.  One common way to control this is to set GRUB_GFXMODE in /etc/default/grub, but maybe you should go straight to grub.cfg and see if it uses that variable.

---

### Post by vascop on 2011-01-18
grub.cfg was explicit in saying I should not edit it. So I went to /etc/default/grub as said there.

uncommented GRUB_GFXMODE and set it to 1024x768. reboot. No difference. set it to 800x600. reboot. No difference.

I was told there to check possible resolutions in grub with vbeinfo. I experimented a bit with the commands. grub sent me to a grub interface where I typed vbeinfo but command was not recognized. Just typing vbeinfo normally is also not recognized.

Any help on the next step? Do I need any drivers or something? (ATI HD5470) I really just want the cli so I thought it was going to be quite easy to set the graphics on this one :P

---

### Post by nothingspecial on 2011-01-18
Did you update grub before you rebooted?

---

### Post by vascop on 2011-01-18
I wasn't aware I needed to. Now I ran update-grub after checking the file, rebooted and still nothing. I guess I'll just live with this resolution

---

