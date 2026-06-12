---
title: "Another VT100 Question"
date: 2009-11-19
forum: General Help
---

### Post by greentoast on 2009-11-19
[COLOR=black][FONT=Verdana]I am looking for an VT100 Emulator for accessing our DEC environment. My work has a very old, but stable, DEC/Alpha/OpenVMS system. We use VT520/400/100 dumb terminals for accessing it. We also have some PCs running Attachmate KEA! in VT100 emulation. KEA is 16bit, built for Windows 95, and works great on windows xp. For security and stability reasons, I would like to convert our few windows PCs, and start any new ones, to Ubuntu.  I have tried a number of emulators and so far have not found one that will display our screens in a usable format. I have tried using Wine but I keep getting OLE errors and have yet been able to resolve them. Short story looong, I would love to find a native VT100 emulator that will work in our environment. Thanks in advance for any help and/or advice.[/FONT][/COLOR]

---

### Post by Giblet5 on 2009-11-19
You already have one.

Open a terminal window and enter the command: ```
xterm
```

It is fully VT100/101 compatible and VT102 is 'close enough', although you may need to set better resources for fonts and preferred PFn keys.

xterm is very capable, but it's old-school X11 stuff where you configure it via resources or command line options. ```
man xterm
```

---

### Post by greentoast on 2009-11-19
I have tried xterm and have not had any luck with it. It will connect, but all of the menus and sub-menus are just random text.

---

### Post by Giblet5 on 2009-11-19
> **greentoast said:**
> I have tried xterm and have not had any luck with it. It will connect, but all of the menus and sub-menus are just random text.

Don't use the menus. Use command line options and resources - or don't use KDE or Gnome...

A good way to use xterm is with other Xt-based sessions like fvwm, lesstif, or Motif if you can get it. libXt is as high up the food chain as xterm goes. Gnome, KDE, and compiz will really mess up Xt applications...

You can try konsole, but its VT100 emulation is only compatible in as far as some ANSI escape sequences coincide. It won't work on a VAX or OpenVMS box.

Xterm is what there is. There's Xvt, but you'll decide that xterm is a lot better. There's nothing you could do in the xterm menu that can't be done with resource settings, and there are quite a few things you can do with resources that aren't available in the menu.

Cheers and good luck!

Edit:
Example command line:
```
xterm -font r24 -fg wheat -bg midnightblue
```

Example entries in ~/.Xresources:
```
...
XTerm*font: r24
XTerm*foreground: wheat
XTerm*background: midnightblue
...
```

(You have to explicitly load those or restart the X server) ```
xrdb .Xresources
``` will load them up. Then "xterm" will just start that way from now on, unless you override the resources via command line arguments.

You now know a deep dark secret about Xorg that about 1:10000 other people know...

For a LOT more info, see ```
man X
``` and for a LOT more info - except in English - see "The X Window System - Volume III" by O'Reilly & Associates (I wrote parts of it!)

---

### Post by falconindy on 2009-11-19
You can set xterm to behave as vt100 with a simple addition:
```
echo "xterm*termtype:         vt100" >> $HOME/.Xdefaults
```
(ur)xvt is an amazing terminal if you take the time to setup a reasonable .Xdefaults file.

---

### Post by greentoast on 2009-11-19
The menus i am refering to are the menus in the terminal emulation itself. The system i am accessing has an text based menu system for accessing information such as part numbers, inventory levels, payables, receiveables, etc. As well as doing our customer billing, inventory receiving and adjusting, etc.

---

### Post by Giblet5 on 2009-11-19
What font are you using for xterm?

It should be one of the rNN fonts, like 'r16'.

If you follow **falconindy**'s advice, xterm WILL emulate a vt100 perfectly, unless you use a variable-width font.

---

### Post by falconindy on 2009-11-19
> **Giblet5 said:**
> What font are you using for xterm?

It should be one of the rNN fonts, like 'r16'.

If you follow **falconindy**'s advice, xterm WILL emulate a vt100 perfectly, unless you use a variable-width font.
Terminus is by far the best fixed-width font I've encountered. I think its included by default with Ubuntu. If its not, install the "console-terminus" package and add more to your .Xdefaults:
```
echo "xterm*font:xft:Terminus:dpi=96" >> .Xdefaults
echo "xterm*boldFont:xft:Terminus:bold:dpi=96" >> .Xdefaults
```

---

### Post by Giblet5 on 2009-11-19
That's installed by default. I'd never used it with xterm though. Thanks!

---

### Post by greentoast on 2009-11-27
I was looking for somthing more point and click. All the users here are used to windows. I gave Wine a try again. The program install goes fine, even the connection setup works. But when it tries to connect, i see the login screen and then get a popup with this error: "OLE - error creating server class factory: error code 0x80040155"
 
Error screen shot:
[IMG]http://www.wmfleetparts.com/broke.jpg[/IMG]
 
what i would like to see:
[IMG]http://www.wmfleetparts.com/working.jpg[/IMG]
 
any ideas?.....

---

