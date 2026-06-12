---
title: "Swedish keyboard layout missing a key"
date: 2006-02-04
forum: General Help
---

### Post by rikard_grankvist on 2006-02-04
Hello. I'm running a standard english language breezy ubuntu. I am however having some trouble with getting the swedish keyboard layout to work. My keyboard is an windows/office optimized keyboard with some fancy buttons for office and browsing etc. I don't see a brand on it, the only title is SMART OFFICE KEYBOARD.

Anywho, the problem is that the "< >"-key doesn't work. On a swedish keyboard the keys to the right of "P" and "L" are reserved for the swedish umlaut letters (Å Ä Ö), and the keys to the right of "M" are ", ;", ". :" and "- _" respectively. Therefore the "< >"-key is moved to the left of Z, right after Shift. That key doesn't work. With the English layout, it works (however, the screen briefly flashes everytime i press it), but with the Swedish layout, it's completely dead.

Also, at every reboot, the layout resets to english, and I have to type "setxkbmap" in a terminal to make it swedish (I don't know exactly what this does, just saw it in some other thread). 

Are these bugs, or have I perhaps set it up the wrong way? In the "Keyboard" preferences dialog, I have english and swedish, with swedish moved to the top and set to default. Any help appreciated, perhaps there's even a fellow swede using ubuntu that can help me... :)

---

### Post by stoffe on 2006-02-04
I don't know why it resets itself like that, but I seem to recall that the missing key issue is just that you've a keyboard configured with one key too little. In said keyboard preference, where it probably says "Generic 104-key PC" or something like that, change it into "Generic 105-key (Intl) PC" and see if that helps.

---

### Post by rikard_grankvist on 2006-02-04
Yeah, I already tried that, but it didn't work. Maybe I need to reboot.

---

### Post by rikard_grankvist on 2006-02-04
Woho!!! That did it. Now I just need to make it remember the layout after rebooting.

---

### Post by stoffe on 2006-02-04
It sounds strange alright. It should "just work" hehe. Anyhow, you probably configured something slightly wrong upon install. You can do```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure Xorg, including keyboard settings. Or you could look manually at [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] - you should have a section looking something like this for swedish keyboard:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
EndSection

```
If XkbModel or XkbLayout says something else, change them and see if that helps.

---

### Post by simosx on 2006-02-04
Why don't you configure the layout through the Keyboard settings?
[http://www.gnome.gr/writing/](http://www.gnome.gr/writing/)

Fiddling with xorg.conf or running setxkbmap is so error prone.

---

### Post by rikard_grankvist on 2006-02-05
[QUOTE=simosx]Why don't you configure the layout through the Keyboard settings?
[http://www.gnome.gr/writing/](http://www.gnome.gr/writing/)[/QUOTE]

Well yeah, that's sorta what I've done. It doesn't seem to work. But now I fixed xorg.conf (which, as you said stoffe, was set up wrong).

---

### Post by stoffe on 2006-02-05
[QUOTE=rikard_grankvist]Well yeah, that's sorta what I've done. It doesn't seem to work. But now I fixed xorg.conf (which, as you said stoffe, was set up wrong).[/QUOTE]
So it works now? Good to hear!

That is one weak point still in a system like Ubuntu - if something is answered wrongly during installation, it may be really hard to beat it back into shape. And since the GUI tools - like Gnome preferences - only act as another layer on top of that, it isn't much they could do.

---

