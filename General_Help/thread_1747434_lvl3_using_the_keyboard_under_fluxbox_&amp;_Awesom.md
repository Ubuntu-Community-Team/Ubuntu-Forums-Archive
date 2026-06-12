---
title: "lvl3: using the keyboard under fluxbox &amp; Awesome"
date: 2011-05-02
forum: General Help
---

### Post by magum on 2011-05-02
Hi @all,

with the new update of ubuntu I thought it was time to try something new, so I started to use Awesome, a really awes..., I mean great windom manager. Stupid thing is only that to program write latex files, or in short to do anything that makes sense I need these keys:
\, |, {, },[,],...

Now because I am working from a macbook pro (pretty old and german layout) I have to change the levels of input from the keyboard. 
\ = <Shift> + <Left_alt> + 7
| = <Left_alt> + 7

Under gnome I have specified these keys in the system configuration. Works nice under gnome, but works not at all under Awesome or fluxbox. (Everytime I try it in a terminal I get: "(arg) 7" instead of "|", which is a little annoying)

So I would assume these window managers use different config files. But where are they?
I edited /etc/default/console-setup:

```
# XKBMODEL="macbook79"
# XKBLAYOUT="de,de"
# XKBVARIANT="mac,mac_nodeadkeys"
# XKBOPTIONS="grp:shift_caps_toggle"
XKBOPTIONS="lvl3:lalt_switch"
```
variable also with "lalt" instead of "lalt_switch" -> no effect

I also looked at /usr/share/X11/xorg.conf.d/ and even created a new xorg.conf with "X -configure" in recovery shell mode. But I have no clue where to start from here.

Any ideas?

---

### Post by magum on 2011-05-03
TL; DR Where can I specify the keyboard layout incl. the lvl3 key for Awesome, fluxbox, etc.?

---

### Post by magum on 2011-05-03
So, I found an version of the xorg.conf at
/usr/share/X11/xorg.conf.d/10-evdev.conf

```

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
     
        # my changes
        Option "XKBMODEL" "macbook79"
        Option "XKBLAYOUT" "de,de"
        Option "XKBVARIANT" "mac,mac_nodeadkeys"
        Option "XKBOPTIONS" "lvl3:lalt"
        Option "XkbOptions" "compose:rwin"
EndSection

```And I uncommented similar lines in /etc/default/console-setup. 
The result: Awesome now thinks I have an english layout o_O

This is exactly the opposite to what I wanted...

---

### Post by magum on 2011-05-04
So thx to the help of a user on the awesome irc, I found the solution:

Try under gnome
setxkbmap -query

and add all these to the 10-evdev.conf described above

---

