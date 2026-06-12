---
title: "Display not working"
date: 2012-09-19
forum: General Help
---

### Post by clay7 on 2012-09-19
...well, kind of. This is on a 12.04 machine that was formerly a desktop environment but lately has been functioning as a server. I'm at the facility now with a monitor plugged in and it will not boot to the desktop. When the computer starts, it gives me a grub boot option, which has always been normal for this computer, and it is displayed in color.

Then, it goes straight to the command terminal.  "startx" does not work...it crashes the system. If I run gnome-panel, I get

> Gtk WARNING: cannot open display: 0

If I run compiz, I get:

> Fatal: couldn't open display: 0

Here's where it gets interesting. Last night I SSH'd in and issued:

> sudo kill -9 xxxx (pid for compiz)

because compiz was eating my CPU. Everything was then fine, from a server standpoint. This afternoon I ran an update and upgrade via SSH, and that's when everything went south. Now I can't get to the desktop.

Other info:

[LIST]
[*]lspci -v   shows the graphics card
[*]/etc/default/grub  is set to "quiet splash" and to show the monitor
[/LIST]

---

### Post by charlezc on 2012-09-19
it seems that the display manager is uninstalled 

when you log in to console type this 

sudo apt-get install ubuntu-desktop

that will install ubuntu gui or desktop enviromnet

also your gonna have to edit the grub default file


sudo nano /etc/default grub
note: to save press CTRL+O and CTRL+X to exit.
look for this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
make sure it says quiet splash under the quotes 
then update your grub
sudo update-grub
then restart:
sudo reboot now

than it should start in desktop enviroment after a reboot

---

### Post by charlezc on 2012-09-19
I made a typo let me correct this 

sudo nano/etc/default/grub and change the line
GRUB_CMDLINE_LINUX="text" to GRUB_CMDLINE_LINUX=""

---

### Post by clay7 on 2012-09-19
Thanks charlezs. I appreciate your help. My /etc/default/grub already had those settings, which I think makes this whole scenario even more curious. Ok, frustrating.

well, now I get the purple Ubuntu splash screen that we all know and love, but after the dots move from left to right, it still goes back to the terminal.

I tried "startx" again and it still locks everything up. I may just do a fresh install since I religiously back up my data. Still would rather not, if anyone has any ideas...

---

