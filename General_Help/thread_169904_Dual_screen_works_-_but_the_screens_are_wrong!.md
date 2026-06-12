---
title: "Dual screen works - but the screens are wrong!"
date: 2006-05-03
forum: General Help
---

### Post by Randomskk on 2006-05-03
After the ATI propri. fglrx driver broke, I decided to go with the open source "ati" driver - not that I had much choice.

Some hacking up of the default xorg.conf and the one I had working perfectly for fglrx later, I managed to get passable dual screen working - with one slight hitch.

The screen that should be on the right is on the left, and the screen on the left is on the right.

It seems that NOTHING I can edit in the xorg.conf file fixes this.
The screens worked like they should have under the fglrx xorg.conf, but with this version - although I can't see anything major that's different - the primary screen works like the secondary, and visa verse.

If I move the mouse to the left edge of what SHOULD be the primary screen, it wraps to the right edge of what SHOULD be the secondary screen - complete backwards.

I don't want to swap the cables around, as although this does seem to fix the problem right off, I've setup.. somewhere.. the screens with AA and text size settings, so that it looks good on both - but I can't find these settings, and running the screens in the wrong sockets means that the CRT has massive text that's heavily anti-aliased, and the LCD has smaller, much worse looking text.

As the screens worked in the right order before, I can't see why I shouldn't be able to get them working properly again.

I've got the working fglrx xorg.conf (that I can't use because the fglrx driver kernel panics on load, and I can't find why), the current xorg.conf (using `ati` drivers) and a picture to explain the incorrect monitor layout.

Any help is greatly appreiciated :)

Image:
[IMG]http://randomskk.net/screen.jpg[/IMG]

Current (ati driver):
[http://randomskk.net/xorg.conf.txt](http://randomskk.net/xorg.conf.txt)

Working fglrx one:
[http://randomskk.net/xorg.conf.fglrx.txt](http://randomskk.net/xorg.conf.fglrx.txt)

---

### Post by ZylGadis on 2006-05-03
I've no experience with ATI (and I don't want to have experience with ATI anyway, my nvidia twinview is perfect), but have you considered something very simple? Physically swap the monitors :)

---

### Post by Ramses de Norre on 2006-05-03
Or the connectors:) even more easy.

EDIT: I should have read through your whole post..

---

### Post by Randomskk on 2006-05-03
I've tried that, but..
[QUOTE=Randomskk]
I don't want to swap the cables around, as although this does seem to fix the problem right off, I've setup.. somewhere.. the screens with AA and text size settings, so that it looks good on both - but I can't find these settings, and running the screens in the wrong sockets means that the CRT has massive text that's heavily anti-aliased, and the LCD has smaller, much worse looking text.
[/QUOTE]

---

### Post by ZylGadis on 2006-05-03
Not the cables. The monitors themselves, keeping the cables in their current sockets :)

---

### Post by Randomskk on 2006-05-03
That would probably work, but I'd rather have the LCD as my primary screen.
I'll probably get a second LCD in a month or so, so I could do that then, but for now I'd rather keep the LCD as primary - it's picture is so much nicer :)

Plus the 19" CRT is heavier than me :P

---

### Post by ZylGadis on 2006-05-03
Perhaps it is different for ATI, but in my setup it does not really matter which monitor is primary.

---

### Post by Randomskk on 2006-05-03
Basically, the connection the CRT plugs into has been set so it looks nice on the CRT - and thus looks shoddy on the LCD - and the connection the LCD plugs into is setup for the LCD, so looks silly on the CRT.
I'd rather have the LCD as primary since it looks nicer anyway, and this setup worked out of the box on the other driver, it just seems that the `ati` driver reverses the order, and I'm not sure where to go to change it, as changing the xorg.conf doesn't seem to help.

---

### Post by Randomskk on 2006-05-03
Well, I finally got it working.
It looks like the ati driver is just preset to use the DVI out as primary, while I needed it secondary.
In the end, I got the old fglrx (included in repos) working with a new libdri or something, and generated a new xorg.conf with the old tool fglrxconfig.

It works, at least :)

---

