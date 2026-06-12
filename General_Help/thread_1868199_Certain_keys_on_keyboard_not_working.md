---
title: "Certain keys on keyboard not working"
date: 2011-10-23
forum: General Help
---

### Post by euphgeek on 2011-10-23
Since upgrading to 11.10, the down arrow and end keys on my keyboard are not working.  It doesn't matter if I use the local keyboard, which is a Microsoft Natural Ergonomic Keyboard 4000 that worked in 11.04, or if I'm logged in from another computer through Gnome Desktop Sharing.  This happens no matter if I'm using Gnome or Unity.  However, when I bring up the keyboard layout, all the keys light up when I press them.  Has anyone else heard of this issue?

---

### Post by euphgeek on 2012-09-16
I'm still having this issue, but I've found a workaround.  If I run the following script after every reboot and after logging into Gnome, the problem is solved (at least until the next reboot):

```

#!/bin/bash
xmodmap -e 'keycode 115 = End'
xmodmap -e 'keycode 116 = Down'

```

---

### Post by ggallozz on 2012-10-08
someone can eXplain why (have to use that script) ?!
(my X is uppercase because my lowercase doesn't work ... after newly installed 11.10)

notice that my [X] lowercase key works normally on a non graphic console (say in CTRL+ALT+F1 )

---

### Post by euphgeek on 2012-10-08
It's the same with me.  The End and Down Arrow keys work in a non-graphic console, but not in Gnome.  I'm sure if you ran the following your 'x' key would work:

xmodmap -e 'keycode 53 = x'

Note: Your keycode number might not be 53.  Use xev to find out which number it is.

---

### Post by ggallozz on 2012-10-10
@[euphgeek]("http://ubuntuforums.org/member.php?u=702199") thanks, 
my keycode also is 53, but the workaround didn't work for me ...

Also doesn't work in a Gnome shell console, only in a pure teXt console as per CTRL-ALT-F1

the capital always work fine, as said in my previous post

---

### Post by euphgeek on 2012-10-10
Just wondering, when you press your 'x' key in xev to find the keycode, does it look like this:

```
KeyPress event, serial 33, synthetic NO, window 0x6200001,
    root 0xbb, subw 0x0, time 729407448, (923,772), root:(929,844),
    state 0x11, keycode 53 (keysym 0x58, X), same_screen YES,
    XLookupString gives 1 bytes: (58) "X"
    XmbLookupString gives 1 bytes: (58) "X"
    XFilterEvent returns: False
```

Or does it look like this:

```
KeyPress event, serial 33, synthetic NO, window 0x6200001,
    root 0xbb, subw 0x0, time 729409264, (923,772), root:(929,844),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XmbLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False
```

Also, does using the "Shift" key change the capitalization of the X key?

---

### Post by ggallozz on 2012-10-10
Xev gives this, for capital X

```
KeyPress event, serial 32, synthetic NO, window 0x4600001,
    root 0x111, subw 0x0, time 626856, (163,-90), root:(824,122),
    state 0x11, keycode 53 (keysym 0x58, X), same_screen YES,
    XLookupString gives 1 bytes: (58) "X"
    XmbLookupString gives 1 bytes: (58) "X"
    XFilterEvent returns: False

```

nothing similar for lowercase, just feels the key-release event, says:

```
FocusOut event, serial 32, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


```

---

### Post by euphgeek on 2012-10-10
What happens when you use Shift or CapsLock and type an 'x'?  Is it still capitalized?  Also, do you have onBoard, the on-screen keyboard, installed?  If so, what happens when you click the 'x' key on that?

---

### Post by ggallozz on 2012-10-10
**SOLVED** this way:

changed the Keyboard Shortcut map!!!
Days ago I did set the desktop "logout" to [Mod4]+[x], this, incredibly, mess up with the simple [x] key ! :-(

I set up now the logout shortcut to [Ctrl]+[x], and simple [x] works back.


:-/

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx !!!!
:-)

---

### Post by euphgeek on 2012-10-10
Excellent!  I'm glad your issue was resolved without resorting to a workaround like mine.

---

### Post by euphgeek on 2012-10-23
With my latest upgrade to 12.10 the issue seems to have resolved itself.  It seems odd, though, that a supposed LTS version like 12.04 would still have the bug in it.  It doesn't make me very confident as to what Ubuntu decides to call LTS.  Not just because of this issue, either.

---

