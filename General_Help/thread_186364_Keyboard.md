---
title: "Keyboard"
date: 2006-06-01
forum: General Help
---

### Post by sinkxdie on 2006-06-01
I just bought this from 

[http://www.logisyscomputer.com/viewsku.asp?SKUID=KB603CL&DID=KEYBOARD](http://www.logisyscomputer.com/viewsku.asp?SKUID=KB603CL&DID=KEYBOARD)

and i kind of need a little help.

I plugged it in, and the basic regular keys work. All the top multimedia keys don't work at all, and the Power, sleep, wake up keys don't either. And by the way, it is a 107-key keyboard. It came with a floppy disk that contained a setup.exe so I didn't even bother.

---

### Post by tonyr on 2006-06-01
What does /etc/X11/xorg.conf say about **Generic Keyboard**?  Mine says
> 
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection


If yours doesn't say **pc107**, try changing it.

---

### Post by sinkxdie on 2006-06-01
Well, I dont know exactly if it **is** a 107-key anymore. When I opened up "xev" it said that the multimedia keys were at numbers such as 233.

Ill definitly try your suggestion now though, and by the way it looks like this now, 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
```

---

### Post by meng on 2006-06-01
You should be able to keep the same keyboard layout and use metacity to map those keys to the desired shortcuts.

---

### Post by sinkxdie on 2006-06-01
```
KeyRelease event, serial 29, synthetic NO, window 0x2600001,
    root 0x4c, subw 0x0, time 2459954597, (-94,359), root:(504,384),
    state 0x0, keycode 234 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
```

is what happens when I press one of my back buttons on the multimedia keys. 

by the way, this is what the row of multi-keys look like
[IMG]http://www.powerpackedpc.com/Pages/images/logisys_keyboard_006.jpg[/IMG]

and that is all on this keyboard, 
[IMG]http://www.logisyscomputer.com/images/SKUImages/KB501CL_01.jpg[/IMG]

---

### Post by sinkxdie on 2006-06-01
How do I use metaciy, is it just like another X, do I have to ctrl+alt+backspace out of my current KDE session and open it in a tty?

---

### Post by meng on 2006-06-01
Actually I'm not sure now I see you have KDE not GNOME. You may have to xmodmap (now you know what codes are generated under xev) yourself. Unless you can use Settings > Regional > Keyboard Shortcuts to add the keybindings in, but it's been years since I used KDE.

---

### Post by sinkxdie on 2006-06-01
Can somebody give me like a step by step way to do this or something judging the pictures that I gave you?

---

### Post by tonyr on 2006-06-01
Another suggestion.  Look in **/etc/X11/xkb/rules/xorg.lst** and see if any of
the keyboard types there match yours.  If you find one, use that to replace
**pc104**.

EDIT:  Your multimedia keys seem to be internet browser oriented, according to
the link you supplied, so I would start with the ones that say **multimedia** or **internet**.

---

### Post by sinkxdie on 2006-06-01
ok, I just want to be able to set the codesusing xmodmap
i can use xev and find the keycode, just what would be the thing to put into the command line to, lets say, use one of the keys to play/pause in amarok.

---

### Post by tonyr on 2006-06-01
It doesn't seem to be that straightforward.  Look at this:
[http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html]("http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html")

EDIT: ...and here are some more:
[https://wiki.ubuntu.com/KDEMultimediaKeys]("https://wiki.ubuntu.com/KDEMultimediaKeys")
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys")

---

### Post by sinkxdie on 2006-06-02
I got it!

It took a long and hard struggle, but I eventually just opened up my 
/usr/share/X11/XKeysymDB
and my /home/*usrname*/*createdfile=""".Xmodmap"""
and i added a keycode equivilant for an XF86 command for something that didn't work, like XF86LightBulb
then I went into systemsettings>regional>keyboard shortcuts
then i pressed the buton and it came up as "XF86LightBulb" for a shortcut to konqueror
so when I press the, standby key in my case, it thinks its opening up XF86LightBulb but it is actually opening up konqueror
        ...well not **exactly** but i like to think of it that way, :D

then what I did was create a script to run that .xmodmap in my /home/*usrname*/env and cronned that to start-up.

---

