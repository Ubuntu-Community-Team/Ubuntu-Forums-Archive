---
title: "Persistent language support"
date: 2011-10-30
forum: General Help
---

### Post by bryncoles on 2011-10-30
Greetings fellows!  

I'm currently playing about with Lubuntu -- my new best friend.  I have it installed as a live USB, so I can make changes to the system, set it up how I like it and then get it installed.   

I'm currently trying to set up dual language support, and while I suspect the problem might be due to the live USB, I'd like to know for sure.  

So, the problem:  I want a dual language system -- (British) English and Greek.  I have Greek installed, I have the language switcher applet in the bottom panel.  It didn't switch the languages for me until I opened 

```
/usr/share/X11/xorg.conf.d/10-evdev.conf
```

and added

```
Option "Xkblayout" "gb, gr"
	Option "kbOptions" "grp:alt_shift_toggle"
```

to the section 

```
Section "InputClass"
	Identifier "evdev keyboard catchall"
	MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection
```

(stick it between 'Driver "evdev"' and 'EndSection', in case you're wondering). 

Now however, half my system menu's are Greek, and half are English.  Furthermore, unless I manually start the language support when I boot the system, I only have US English.  

How can I get the language to be EITHER all English, or all Greek, and how do I ensure the language selection changes persist across boots?

Thanks in advance!

---

### Post by bryncoles on 2011-10-31
bump!

---

