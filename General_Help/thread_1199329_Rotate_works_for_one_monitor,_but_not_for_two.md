---
title: "Rotate works for one monitor, but not for two"
date: 2009-06-28
forum: General Help
---

### Post by daehenoc on 2009-06-28
Hi all,

I've got an R600 Radeon HD2400XT low-profile PCI-E video card in a Dell Optiplex 755.  I've got two 24" monitors attached via DVI with the special splitter cable that comes with this video card.

I want the first display rotated 90 degrees to the left and the second display not rotated.

If I start Gnome with only one monitor attached (to the primary output), I can use the following command to rotate the display 90 degrees:
```
$ xrandr -o left
```
Which is exactly what I want as the Dell monitor can rotate for me.

When Gnome has the second monitor attached and plugged in, I can still rotate the first monitor, but I loose the display on the second monitor :(

Has anyone been able to rotate their primary monitor, but keep normal orientation (and the display!) on their secondary monitor with an ATI HD2400XT?

Cheers,
Greg

---

### Post by t4thfavor on 2009-06-28
Some monitors  have that ability through the mmonitor OS, I have done it that way.

I have never tried to do it through  X as I only have CRT's on mu ubuntu box.

---

### Post by daehenoc on 2009-06-30
Hah, fixed!

I had to set the Xserver Virtual size to '3840 1920'.  X starts with both monitors in normal orientation and I have to open a shell and execute the following commands:
```
# Rotate the left monitor
xrandr --output DVI-0 --rotate left
# Move the right monitor up against the left monitor
xrandr --output DVI-1 --pos 1200x0
```
Once the left monitor is rotated, there is a 720 pixel gap between the monitors, so I have to move the right monitor to position 1200x0 to remove the gap.

There is one problem, on the left monitor, when windows are moved around, there are vertical, single lines left behind when that windows is redrawn upon moving.  It's something that I am prepared to live with :)

Apparently xrandr commands can be executed before gdm starts, so I'll use this for a few days to make sure it's stable before looking into that!

I found some useful information in this thread: [http://ubuntuforums.org/showthread.php?p=7538405](http://ubuntuforums.org/showthread.php?p=7538405)

---

### Post by valenshek on 2009-11-13
I just got this working in Ubuntu 9.10 permanently and through the GUI tools provided.  No running xrandr, and it comes up correctly every time I log on.  But, I did have to edit one file first.  Edit /etc/X11/xorg.conf and in the 
```
SubSection "Display"
     Virtual xxxx yyyy
EndSubSection
```
area, change the yyyy number to the now vertical resolution of the monitor that you've rotated.  For example, the numbers on mine were 3728 and 1152, because I've got a 23" monitor with resolution of 2048 x 1152, and a 20" monitor with resolution of 1680 x 1050.  When I modified this to 3728 1680, this allows my 20" monitor to be rotated.  If I wanted to rotate the 23" monitor, I would have changed the yyyy number to 2048.

After saving this file, log out and log back in.  Now, go the System menu -> Preferences -> Display.  You can now click on the monitor that you wish to rotate, and Left and Right should appear as options in the Rotation section.

---

