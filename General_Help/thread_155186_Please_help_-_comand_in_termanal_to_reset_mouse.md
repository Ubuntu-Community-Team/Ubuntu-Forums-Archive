---
title: "Please help - comand in termanal to reset mouse?"
date: 2006-04-04
forum: General Help
---

### Post by engineering.concepts on 2006-04-04
I have a laptop (IBM T22) and I have an external optical mouse , everything works great, but my laptop mouse (ibm eraser head mouse) does not work when my external mouse is installed. - This is fine - my problem is when I move my laptop somewhere else and I do not need an external mouse. When I unplug my external optical mouse I can not seem to get the laptop mouse working unless I reboot the computer. Is there an easy terminal command to reset the mouse?
I tried
sudo mouseemu
but it did not work.](*,) 
Any ideas?
Thakns.

---

### Post by engineering.concepts on 2006-04-05
This is the output from terminal when I type sudo mouseemu (with the optical mouse attached)

maximus@Maximus:~$ sudo mouseemu
Password:
mouseemu 0.15 (C) Colin Leroy <colin@colino.net>
using (0+0) as middle button, (0+0) as right button, (56) as scroll.
using /dev/uinput.
maximus@Maximus:~$ Trying to open /dev/uinput... error.
Trying to open /dev/uinput... error.
Trying to open /dev/input/uinput... ok.
Trying to open /dev/uinput... error.
Trying to open /dev/uinput... error.
Trying to open /dev/input/uinput... ok.

Any thoughts?

---

### Post by engineering.concepts on 2006-04-18
Half way there - 
Reading other posts on the forum caused me to check out my BIOS. Turns out that IBM has a BIOS setting to turn off the trackpoint once another mouse is plugged in and it does not reset once you unplug the external mouse.
Changed the Bios setting and now I can use both and unplug as I like - only drawback is the external mouse optical scroll feature does not work anymore ....... I know I saw I posting on that somewhere in the forum..........................

---

