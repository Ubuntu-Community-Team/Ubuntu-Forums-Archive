---
title: "Ctrl+Alt+F7 Does not work"
date: 2012-02-28
forum: General Help
---

### Post by devaj on 2012-02-28
Hi,
It recently came to my notice that Ctrl+Alt+F7 is not working,i.e it is not taking me back to gnome session.Ctrl+Alt+[F1-F6] works perfectly.Ctrl+Alt+[F7-F12] no luck.Compiz was never enabled and is disabled right now.
Here are the results of the following commands

**1)ps -ax | grep X**

Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
  897 ?        S      0:00 avahi-daemon: running [phycosis-XP-M5ARC410.local]
 1917 tty1     S+     0:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc :0 -auth /tmp/serverauth.mWLyA12RgO
 1918 tty7     Ss+    0:21 /usr/bin/X -nolisten tcp :0 -auth /tmp/serverauth.mWLyA12RgO
 2447 pts/0    S+     0:00 grep --colour=auto X

**2)setxkbmap -print**

xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+inet(evdev)+terminate(ctrl_alt_bksp)"	};
	xkb_geometry  { include "pc(pc105)"	};
};

**3)xmodmap -pk | grep '(F[0-9]+)'**

This command does not give any result and goes back to the prompt


[B]4)awk '/Section "(InputDevice|ServerFlags)"/,/EndSection/' /etc/X11/xorg.conf
[/B]
Section "ServerFlags"
    Option "DontZap" "false"
EndSection

**5)xmodmap**
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

[B]6)vi /etc/X11/xorg.conf
[/B]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "IgnoreEDID" "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerFlags"
    Option "DontZap" "false"
EndSection

The Ctrl+Alt+F7/F8 used to work properly before on this installation.
The legacy/proprietary driver for my graphic card (radeon x200) is no longer supported by current x-server/xorg.Hence using the default.Desktop is Ubuntu 10.10.
I would be greatful if someone could help me out here.
(Been a long day today,gotta catch some sleep.Will look up tomorrow.)
GOD speed to all.

---

### Post by devaj on 2012-02-29
[bump]
I have searched all over the net but could not find a relevant solution.Please help.

---

