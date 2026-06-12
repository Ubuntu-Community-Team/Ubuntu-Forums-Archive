---
title: "Emulate right-mouse-click with hardware button?"
date: 2010-07-25
forum: General Help
---

### Post by GroovingClockwork on 2010-07-25
Hello,

I would like to assign right-mouse-click behaviour to a hardware button. I can associate a keypress, or a combination of keypresses with an  "xdotool click 3" command via the Gnome keyboard shortcuts.

I have the scancode of the hardware button so can use

setkeycodes scancode keycode

to mimic any key of my keyboard. However, I don't want the hardware button to mimic a single key of my  keyboard that is already in use, since then the keyboard key will also activate xdotool.

So I think I need:
- either a way to associate that particular scancode with an (outlandish) keypress *combo* rather than a single keypress;
- or a keycode which is not currently in use, to bind to the scancode. Are there any like that and how would I find out? In the Gnome Keyboard Shortcuts list there is stuff like "XF86AudioMedia" which I'm not using -- but does that correspond to a numerical keycode value which setkeycodes understands?

Thanks for considering.

---

### Post by theOGRE on 2010-07-25
I don't know, but xev might help. It reports your keypress events.

---

### Post by theOGRE on 2010-07-25
Or maybe look at your layout's xmodmap file in /usr/share/xmodmap/???

---

### Post by AlphaLexman on 2010-07-25
Where are you located?
What is your keyboard layout?

---

### Post by limestone on 2010-07-25
check this out
[http://ubuntuforums.org/showthread.php?t=1463005](http://ubuntuforums.org/showthread.php?t=1463005)

---

### Post by GroovingClockwork on 2010-07-25
Thanks for the replies folks.

I have a UK keyboard; however the button I'm trying to configure is on the (mobile) computer itself, not on the keyboard.

Incidentally, what's up with the keycodes given by *xev* and xmodmap.uk (e.g. 24 for 'Q') are +8 compared to the ones given by *showkey -k* and used by *setkeycodes* (16 for 'Q')? 

In any case xmodmap.uk doesn't list special keys like the 'menu' keyboard key which *xev* gives as having keycode 135. And *xev* and *showkey* can only tell you which keycode goes with a key which already has a keycode assigned, not which keycodes are still available...?

I made a guess and supposed keycode 134 (126 to *showkey*) was available. So I did

```
sudo setkeycodes e078 126
```

where e078 is the button's scancode. So far so good, if that doesn't overwrite some existing key...

Installed mouseemu (see pont.andersson's thread) and did

```
mouseemu -right 0 134
```

That gave

mouseemu: can't open /var/run/mouseemu.pid: permission denied
open: No such file or directory
No uinput device found! Make sure the uinput module is loaded
or CONFIG_INPUT_UINPUT is compiled into the kernel.

Trying the same command as above preceded by sudo gives no messages whatsoever, and the desired effect doesn't occur (button is unresponsive).

Following [this]("http://ubuntuforums.org/showthread.php?t=478065") I did

```
sudo modprobe uinput
```

to add the module to the kernel but that doesn't change any of the above (though the uniput module is listed when I do *lsmod*).

... Any more thoughts? Thanks.

---

### Post by theOGRE on 2010-07-25
I got nothing. I just through xev out there 'cause I remembered hearing about it and keycodes once. I hope you figure it out. I have a couple useless buttons that I wouldn't mind putting to work.

---

### Post by GroovingClockwork on 2010-07-26
I got a bit further thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=109377") (theOGRE, have a look at that), but not quite there yet.

It doesn't look like *dumpkeys* as suggested by that thread gives me an accurate list of which keycodes have already been taken and which are available (it also spams the console screen, though that can be mended by sending the output to a file, as in *sudo dumpkeys > dumpkeys.output*). I have more trust in /usr/include/linux/input.h which for instance says "#define KEY_RIGHTMETA 126" and indeed *xev* returns 134 (= 126 + 8) when I press the right 'Windows' key.

So now I know I shouldn't assign keycode 126 to my button, instead I do

```
sudo setkeycodes e078 184
```where 184 corresponds to KEY_F14 in input.h -- I'm assuming this is unused.

Next step is to bind the right-click command to this keycode. The thread I linked to explains this well. *xev* tells me that my 126 (or 134) keycode is linked to the keysym X86Launch5, so in gconf-editor, I set /apps/metacity/global_keybindings/run_command_1 to the value *X86Launch5*, and I set /apps/metacity/keybinding_commands/command_1 to *xdotool click 3*. (Note you may need to install xdotool for this to do anything.)

The result: I get right-click behaviour out of my hardware button, but it's very inconsistent:
* On Gnome GUI elements (e.g. the window borders, desktop icons) I need to hold the button a fair while for the pseudo right-click to happen: less than a second, but longer than just a quick push on the button as one would normally do. In contrast, if I substitute, say *xeyes* for *xdotool click 3*, I can conjure up googly eyes on my screen at lightning speed :/
* In GIMP, a pseudo-right click on the canvas does nothing (it should bring up a menu). [Edit: if I hold the button a very specific length of time, it actually works - but this is impossible to time with any consistency.]
* In MyPaint, Firefox and Thunderbird a quick pseudo-right click does exactly what it needs to.
* In Google Earth, right-clicking on the globe and then moving the mouse down or up zooms/unzooms; with my pseudo-right-click it behaves weirdly and mostly just unzooms.

... so, not quite there yet. This may be due to limitations of xdotool, or perhaps some apps look for a more direct 'true' right-click signal and are confused by the pseudo right-click that metacity tries to serve them...?

Any more insights still very welcome.

---

