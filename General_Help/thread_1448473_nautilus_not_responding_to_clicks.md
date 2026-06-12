---
title: "nautilus not responding to clicks"
date: 2010-04-06
forum: General Help
---

### Post by mdshann on 2010-04-06
I am having a strange problem with nautilus when I try to go up on level using either the up arrow or the breadcrumbs the button depresses when I click it but nothing happens. If I sit there and click click click about 2 dozen times it will finally respond. I just noticed this today. The machine in question is running 9.10. Maybe this computer is just junk, I mean it only has a 2.8 Ghz Pentium D. LAWLZ

---

### Post by duanedesign on 2010-04-06
hello mdshann,
you can run **xev** to test whether a keypress event is seen. In a Terminal (applications > Accessories > Terminal) run the command:

```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

A little white box will appear. Press the key in question and you should see some output to the Terminal that looks like this:

```
keycode 111 = (keysym 0xff52, Up), state = 0x0
```

That is my key up.
Close the white box 'Event Tester' when done to stop xev.
Let us know what you get.

---

### Post by mdshann on 2010-04-06
The command you gave me doesn't seem to register mouse clicks. Is that correct? I am able to use the mouse normally in other windows. In fact in nautilus it works fine sometimes as well. I just looked at the system monitor and nautilus it currently using 246 MB of RAM. Is this normal? I only have one window open and no file operations at this time.

Oh and some more info about the machine: It registers in system monitor as 875 MB or so of ram. I believe this is due to having 128 MB set in BIOS for the shared video. The machine just seems to be sluggish in general. When I first built it it was fine.

---

