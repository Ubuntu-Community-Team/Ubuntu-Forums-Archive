---
title: "German keyboard layout broken"
date: 2010-09-29
forum: General Help
---

### Post by dr4ziw on 2010-09-29
Hi, all.
Got a little problem with my keyboard layout (de -- German; all variants).
Everything worked fine until a few days ago. I noticed that the tilde (usually accessible via [AltGr]+[+]) doesn't work any more. What it shows instead is the "bracketright". 
Even worse, almost every AltGr combination seems to have changed -- the brackets enclosing AltGr and + in the former sentence were achieved by "AltGR"+"ü" (left) and "AltGr"+"+" (right).

Here's what gnome-keyboard-properties looks like, when I select any German keyboard layout -- minus "insert", "delete", ... and the num block:
[IMG]http://img96.imageshack.us/img96/1962/xkbde.png[/IMG]

Not only has the tilde disappeared from its regular position, it can't be found anywhere on the keyboard. This holds true from the login screen to the regular workspace. Switching to tty1..6 or booting up a VM, everything works fine.  

Any ideas, how this could happen? AFAIR, I didn't touch anything which affects the keyboard layout -- or is dpgk-reconfigure fontconfig doing something like this? ^^

- dr4ziw -

P.S. Tried to dpkg-reconfigure xserver-xorg... Shouldn't there be some dialog popping up?? It's dropping me directly back to the prompt.

---

### Post by dr4ziw on 2010-09-29
Okay, I seem to have found the culprit for the broken layout.
Had to install a clean Ubuntu 10.04 into a VM, but anyway. ;)

When I issue ```
setxkbmap -print
``` inside the VM-Ubuntu I get the following:
```

xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwertz)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+de+inet(evdev)"    };
    xkb_geometry  { include "pc(pc104)"    };
};

```On my physical machine however, the same command delivers this output:
```

xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwertz)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+de+inet(evdev)+typo(base)"    };
    xkb_geometry  { include "pc(pc104)"    };
};

```Note the additional "typo(base)"! 
Two questions I can't answer at the moment:

[LIST=1]
[*]How can I remove this? That is, I need to know where this include line is stored.
[*]Where the **** is this typo(base) coming from?!
[/LIST]
Any suggestions on question 1?

About the second question, typo(base) seems to be a keymap developed by some Russian guy, apparently to have better access to typographic symbols. So far so good, but since I didn't know about that layout, I'm pretty sure that I did not choose to use it. 
However, since this layout is displayed in the gnome-keyboard-properties, when I try to add another keyboard layout, like de(nodeadkeys), would it be possible that typo(base) somehow got compiled into de(*)... xkbcomp? If so, how could this be reverted?

*sigh*
Hate to say that, but.. heeelp please!!! :D

---

### Post by dr4ziw on 2010-09-30
*bump*  ...   but not without a little update.

Here it goes:
From what I've learned so far, typo(base) can be enabled via the compatibility options ("enable extra typographic characters") in the gnome-keyboard-proberties, just like CTRL+ALT+BACKSPACE to kill the X server.
Fine! But it is NOT enabled there, and still it is always present and can't be disabled. Instead, typo(base) now acts as the default keymap for the third (AltGr) and fourth (AltGr+Shift) keyboard layer -- cf. screenshot in my first posting in this thread.
WHY?!

However, I have found a temporary workaround for this issue.
After the system is up and running, I have to switch the USB port of a device.  ANY device, that is. It doesn't matter, if it is the USB keyboard or the powered off external HDD. As soon as I unplug one of these devices and replug them into another port the keymap is working as it should. 

Proof: 
Unplug external HDD, replug into another free port...
*pressing AltGr +(twice) =* ~

Now I open gnome-keyboard-properties, and only switch from pc(105) to evdev
*pressing AltGr +(twice) =* ]]

Back to pc(105)...
*pressing AltGr +(twice) =* ]]

Unplug external HDD again, and replug into first port...
*pressing AltGr +(twice) =* ~
(q.e.d.)

Apparently, this works only once in every session until every USB port is misconfigured, or whatever.

I'm rebooting now, and will try the same procedure with the keyboard.

---

### Post by dr4ziw on 2010-09-30
> **dr4ziw said:**
> 
Apparently, this works only once in every session until every USB port is misconfigured, or whatever.

Yeah, forget about that! I works only once at all... Not anymore, now.

How can I get rid of this stupid typo(base) thing?
At best without reinstalling the whole OS...

---

### Post by dr4ziw on 2010-09-30
Solved! 
 
Still don't know why, but somehow the "misc:typo"-switch got written into  
```
~/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml
```and decided to stay there.
Removed the entry with the gconf-editor, and immediately the tilde and all the other keys started working correctly again; also after a reboot, and also when I change something in the keyboard properties -- add, remove, options, etc. The keyboard layout preview inside the "add" dialog is also showing the correct mapping.

---

### Post by roy.nico on 2012-01-03
Your solution is black magic, but thanks a lot !! I have been fighting with exactly the same problem for months. 
If you have any idea about, what did  "misc:typo" mean, i'm very interested !
Thanks again, you really saved my life : since several months i'm doing intensive LaTeX development ... and without {[\ it was like a nightmare !

Nicolas

---

### Post by dr4ziw on 2012-01-03
Hi, Nicolas!

Good to see that I'm not the only one to experience this problem. And I'm very glad that my solution helped.

Concerning "misc:typo"…
I'm not **entirely** sure, but AFAIK that switch is supposed to provide you with easier access to special typographic characters. What I **do** know is, that it shouldn't be impossible to disable the darn thing again ;)

Cheers!

---

### Post by roy.nico on 2012-01-03
If understood you correctly, your system used to work correctly, but at some point, the special characters stopped to work. For me, the same. I just did not notice when exactly.
I was also happy to see, that i was not the same with this problem :)
nicolas

---

### Post by dr4ziw on 2012-01-04
Actually it was the other way round. I never enabled this special typographic keyboard layout. That is, not that I remember. I might have tried it once, and didn't notice that I wasn't able to turn it off again.

However, if you look at the screenshot in the very first posting of this thread, you can see that the Guillemets are not only present on [AltGr]+[y] and [x] -- where they are obviously very handy, especially for LaTeX with \usepackage{csquotes} and autoquote set to [»] and [«] ;) -- but also on [AltGr]+[,] and [.], where I definitely don't like them.

Cheers!

---

