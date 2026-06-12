---
title: "Ubuntu Install Error - Graphcis Card"
date: 2006-04-20
forum: General Help
---

### Post by Hieros on 2006-04-20
When I attempt to install Ubuntu on my new Dell E510, I get an error saying there is something wrong with the graphics card, then the screen gets covered in the phrase ubuntu@ubuntu... I don't know what either really says, it happens really fast. Then I if I push enough buttons i get to a screen that says 'reboot y/n?' I'm assuming it has to do with the fact my graphics card is an ATI Radeon X300 w/Hypermem. Is it possible to rectify this situation now? I was going to get a different graphics card anyway, but I would like to install it now.

---

### Post by cowmix on 2006-04-20
I am having a similar issue..  when the install is done and it reboots.. and then I get a X Windows error.. X doesn't come up at all.  I have the same config as the above post and the 2007FPW monitor too...

Here is a copy of my [Xorg.log]("http://cowmix.com/Ubuntu/Dapper/Xorg-0-log.txt") file..

Knoppix 4.0.2 boots fine under X... if that means anything.

---

### Post by nanotube on 2006-04-21
well, first thing to try is to change the device in your /etc/X11/xorg.conf to 'vesa'. find the line that looks like 
```
Device "ati"
```
and change to 
```
Device "vesa"
```
give it a good reboot (or just try "startx" from the command line), and see if that works. vesa is kind of the "failsafe" gfx device, if it doesnt work with that, it wont work with anything, kind of thing. :)

---

