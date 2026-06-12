---
title: "XKB - Keyboard Problems"
date: 2006-03-23
forum: General Help
---

### Post by noumaan on 2006-03-23
I wanted to install Phonetic Urdu Keyboard instead of what I had installed with ubuntu default installation. I previously followed the directions from the page mentioned below and they worked, (but then I had to format my hard disk) So again I followed directions from this page: 
[https://wiki.ubuntu.com/UrduKeyboard](https://wiki.ubuntu.com/UrduKeyboard)

I dont know what went wrong but Installation failed and since then I am seeing these errors whenever I try to do anything with my keyboard layout preferences: 

```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

```

I ran the two command mentioned and below are the results: 

```

$xprop -root | grep XKB

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "", ""

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

 layouts = [us]
 model =
 overrideSettings = false
 options = [grp grp:alts_toggle]

```
[LIST]
[*]I need help to change my settings to default state
[*]I also need help with installing the phonetic keyboard layout
[/LIST]

---

### Post by noumaan on 2006-03-23
Please I need help :(

---

### Post by Barrakketh on 2006-03-23
You'll either have to wait until someone who has experience with that comes along, or you can try e-mailing the author of that guide.  His gmail address is listed on his [user page](https://wiki.ubuntu.com/CoreyBurger2).

---

### Post by noumaan on 2006-03-23
Ok I have emailed the author aswell.

---

### Post by noumaan on 2006-03-24
Problem Solved. But I did it the hard way. First I had to delete my current ubuntu installation and install it again. Then I went to the guide and did every thing as mentioned but skipped the xkbcomp command which I guess is not supported any more.

---

### Post by vitoko on 2006-04-14
i have the same problem but i fixed.

sudo apt-get install --reinstall xkeyboard-config

---

### Post by nip37 on 2006-05-07
i installed ubuntu and did install urdu keyboard, but for some reasons i had to delete  ubuntu, after i reinstall ubuntu and trying to install urdu keyboard i am getting the same error? is it possible if i can fix it with out deleting and reinstalling them?

---

### Post by nip37 on 2006-05-07
may be this is the problem in urdu keyboard installation page it says
copy this file to
/etc/X11/xkb/symbols/pc folders
but i dont find any folder named "pc" in here instead i have one txt file named "pc"?
how can i recover this?

---

### Post by noumaan on 2006-05-08
[QUOTE=nip37]may be this is the problem in urdu keyboard installation page it says
copy this file to
/etc/X11/xkb/symbols/pc folders
but i dont find any folder named "pc" in here instead i have one txt file named "pc"?
how can i recover this?[/QUOTE]

Nip27 you are right, don't paste the 'ur' file into pc folder paste it only in symbols folder. follow rest of the instructions. if u face any problems please report here.

---

### Post by dantum on 2006-05-10
Hi,

I had the same problem and i managed to fix it but going into keyboard setup menu in System->Prefferences_Keyboard. There I changed keyboard from my default to anther one. This game me an error message. After that i selected the original keyboard. Then i pressed reset to defaults.

I also noticed that in gconf-editor in desktop->peripherals->keyboard->kbd 
All entries should be blank. You can run gconf-editor while you are changing keyboard layouts. The moment the entries go away, stop. Then log off from X and log back in. 

The error went away for me after this.

---

