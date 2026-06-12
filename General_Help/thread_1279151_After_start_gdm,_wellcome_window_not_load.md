---
title: "After start gdm, wellcome window not load"
date: 2009-09-30
forum: General Help
---

### Post by s2s on 2009-09-30
Hello,
two days ago i have problem on my laptop, when gdm start, i have nvidia logo and then black screen with mouse cursor who i can move (this corsor have picture of circle with point around, usually this cursor i look when system say me waiting!), and black screen stay approximately one-two minutes, then screen show me terminal (on 1 second) and again come back to nvidia logo and then black screen with thinking mouse...and this continuously always.

My ubuntu 9.04 have kernel 2.6.28-15-generic.

Befor this problem i install "LAMP SERVER" (from synaptic in "edit->mark packages by task").
Compiled "glib-2.14.6" and make install (from there: [http://linux.softpedia.com/progDownload/GLib2-Download-2653.html](http://linux.softpedia.com/progDownload/GLib2-Download-2653.html)).
And may be more packets, but now i can't remember this..

In /var/log/gdm i have this:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux localhost.localdomain 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
   Before reporting problems, check http://wiki.x.org
   to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 29 17:14:44 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple definitions of the FOUR_LEVEL_KEYPAD key type
>                   Earlier definition ignored
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple definitions of the FOUR_LEVEL_KEYPAD key type
>                   Earlier definition ignored
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple definitions of the FOUR_LEVEL_KEYPAD key type
>                   Earlier definition ignored
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple definitions of the FOUR_LEVEL_KEYPAD key type
>                   Earlier definition ignored
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Multiple definitions of the FOUR_LEVEL_KEYPAD key type
>                   Earlier definition ignored
Errors from xkbcomp are not fatal to the X server
 ddxSigGiveUp: Closing log

```

I can't solved this problem third day... any body can give me key/hint to solved this problem?

---

