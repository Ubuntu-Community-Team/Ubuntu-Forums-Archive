---
title: "Ubuntu errors"
date: 2012-09-07
forum: General Help
---

### Post by stookin on 2012-09-07
hi

I am in trouble.

- When I start Ubuntu, it freezes for about 2 minutes before I can enter the password or choose a user at the login screen.
-  The sound icon in the top right is not working, I can't turn the volume  up. the volume slide bar is stuck at about 3 percent and I am unable to  mute
- music can not be played except with a crackling sound or no  sound in VLC. When I start Rhythmbox it freezes at first for a few  minutes. When I try VLC I get the error message:
"  [COLOR=#ff0000]Audio output failed:[/COLOR]
 [COLOR=#000000]The audio device "default" could not be used:[/COLOR]
 [COLOR=#000000]Connection refused.[/COLOR]
 [COLOR=#000000]
[/COLOR]
"
After  the freeze however, Rhythmbox does play the mp3 file with good clear  sound. It is certainly not at 3% volume it's just normal.

- In  Firefox every context window freezes Firefox for a few minutes (right  mouseclick, when I click noscript, when I click lastpass or any other  add on which gives a context menu when clicking on it)

- skype does not show my webcam nor sends my sound to the person I am skyping with

- this morning I had multiple internal ubuntu errors, I sent them to the support.
I tried uninstalling skype because the problem was probably stemming from installing skype this morning.

- I reinstalled skype

- I tried clearing my machine up by running bleachbit and running this in terminal:
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

- context menu does however work perfectly in ubuntu itself or programs like gedit/geany and others

- sometimes when I work with heroku and I try to git push the content up to their server with this command: "git push heroku master"
I receive this error message sporadically:
ssh: connect to host heroku.com port 22: Connection refused fatal: The remote end hung up unexpectedly

exiting terminal and restarting, or rebooting the computer does not fix this problem. Once it happens the error stays there and I can't do anything.
however usually waiting like half a day or the next day this problem is gone again :s after my computer has been off for a while
my computer is 7 years old and I use it a lot. So maybe this is a hardware issue. But still what could it be?
It's not overclocked or modified in any way.

I am running ubuntu 12.04 and the software is up to date

Please help

edit:
in the top right there's a speaker icon and there used to be like these things ))) which indicated it's volume.
now it's the speaker icon followed by 3 ---
so like this:
SpeakerIcon ---
I hope you understand what I mean..

edit 2:
firefox freezes with context menus and javascript alerts

---

### Post by Epodx64 on 2012-09-07
What video card are you using?

---

### Post by stookin on 2012-09-07
> **Epodx64 said:**
> What video card are you using?

Radeon X1600/X1650 PRO


  *-display:0             
       description: VGA compatible controller
       product: RV530LE [Radeon X1600/X1650 PRO]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:24 memory:c0000000-cfffffff memory:dfef0000-dfefffff ioport:bc00(size=256) memory:dfe00000-dfe1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV530LE [Radeon X1650 PRO] (Secondary)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfee0000-dfeeffff

by the way, it seems to have repaired itself :s everything seems normal again
The sound icon is back to normal and firefox doesn't freeze anymore on context menu's or alerts
I don't know what is going on

---

### Post by Epodx64 on 2012-09-08
Did you update your system at all? maybe that fixed it? could be a hardware issue

---

