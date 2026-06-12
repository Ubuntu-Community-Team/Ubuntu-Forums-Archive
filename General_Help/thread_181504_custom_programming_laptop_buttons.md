---
title: "custom programming laptop buttons"
date: 2006-05-24
forum: General Help
---

### Post by 0MG on 2006-05-24
I was wondering what I need to do to program the buttons that don't function under ubuntu on my laptop. I have one button that will change the processor speed between 1.6 ghz and 800 mhz. I have been able to get this set up through a help page at linux on laptops. That helped quite a bit.

There is another button that normally opens Windows Media Player under XP/Win. I would like to set it up to open a different program under linux. Anyone have any insight on how to get this to happen? I think I need to find out what call takes place when the button is pressed.

Appreciate any advice.

edit: if it helps at all, I am using an Averatec AV4155.

---

### Post by glinsvad on 2006-05-24
I used to bind keys with xmodmap in Kubuntu, but moved to Ubuntu where they just work - so haven't tried the following in Ubuntu yet...

First you need to figure out which keycode is associated with the key you wish to bind. Using xev a window will come up; when focused it will output keycodes corresponding to keypresses (along with a whole lot of useless junk).
```

xev

```

Next you will need to know the predefined symbol of the action you want the keystroke to perform. Look in /usr/share/X11/XKeysymDB for something like XF86blahblah.

Now as root create a textfile /etc/X11/Xmodmap and type in "keycode <keycode> = <symbol>" with <keycode> replaced by the number you found using xev, and <symbol> with the action like XF86blahblah. I used these bindings:
```

keycode 160 = XF86AudioMute
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
keycode 178 = XF86WWW
keycode 236 = XF86Mail

```

To enable the bindings, run this command in terminal (or restart the X-server perhaps?)
```

xmodmap /etc/X11/Xmodmap

```
Running xev again, you should (hopefully) see that the system recognizes your newly binded keys. 

Finally, tell Ubuntu what that hotkey should do (some actions are predefined). In KDE this was easy because it had a simple GUI somewhere... dunno about Ubuntu though. Try System>Preferences>Keyboard Shortcuts

---

### Post by 0MG on 2006-05-24
Wow. Thanks for the excellent reply. I got it to work!

---

### Post by glinsvad on 2006-05-24
He he I'm just realizing, maybe "Try System>Preferences>Keyboard Shortcuts" was enough to make it work in Ubuntu...

---

### Post by nspidle on 2006-05-24
Great reply but I still cant get mine to work. I have a Toshiba A75 and running xev and pressing all the buttons on the left of my keyboard does nothing. :-( any other ideas?

Edit: normal keyboard keys will display output

---

### Post by glinsvad on 2006-05-26
Have you tested if they are recognized using System>Preferences>Keyboard Shortcuts?

---

### Post by nspidle on 2006-05-26
I think what the problem is that my laptop keyboard is using the "generic 104 keys" driver. I get no response at all on those buttons. not in keyboard shortcuts nor in xev

---

