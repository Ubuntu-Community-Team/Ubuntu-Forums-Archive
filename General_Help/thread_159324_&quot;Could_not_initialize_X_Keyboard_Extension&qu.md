---
title: "&quot;Could not initialize X Keyboard Extension&quot;"
date: 2006-04-12
forum: General Help
---

### Post by v79 on 2006-04-12
Every time I boot up into Gnome, I get an error message: "Could not initialize X Keyboard Extension". It's very annoying.

But more worryingly, my keyboard mapping is wrong - @ and " in the wrong place, ditto \ and # and < and lots of other keyboards.

But I can't change these: in System>Preferences>Keyboard, there are NO Keyboard Models listed, only one layout (us) listed, so I can't change them.

I am using an A4Tech keyboard with a British layout (where's my GBP sign? should be <Shift>3 but I can't find it!).

I'm running Dapper, with XGL/Compiz installed.

Please help!

Liam

---

### Post by v79 on 2006-04-14
Nobody? Bump? How about "Which package contains the Keyboard layout and locale information for Gnome?"

---

### Post by Ramses de Norre on 2006-04-14
Maybe sudo apt-get install keyboards-rg or sudo apt-get install --reinstall keyboards-rg

---

### Post by v79 on 2006-04-15
Hi
Thanks, but that didn't do anything. My System > Preferences > Keyboard > Layout thing is still completely empty.

---

### Post by Ramses de Norre on 2006-04-15
sudo apt-get install --reinstall package_name
for package names try:
console-data
keymapper
xkeysw

Hope one of them helps.. this are some packages that may be relevant to your problem.

---

### Post by PriceChild on 2006-04-15
In windows, this is caused by using the American English keyboard setting layout instead of the UK English one.

Or the other way around maybe depending on where you are :)

Anyway, check your keyboard settings :)


EDIT

Sorry Ramses, didn't read that post where it was mentioned :) Please don't hurt me, although i think my comment is still valid :)

---

### Post by Ramses de Norre on 2006-04-15
The problem is that he hasn't got any possibilities listed there..

---

### Post by v79 on 2006-04-16
Well, i've removed compiz, Xgl, mesa, etc from my system and voila! my keyboard control options suddenly reapper. Although the keyboard mapping is still wrong; I'm working on that.

I've tried to add the UK international keyboard layout and a big error message appears:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

