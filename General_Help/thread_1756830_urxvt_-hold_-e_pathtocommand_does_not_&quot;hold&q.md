---
title: "urxvt -hold -e path/to/command does not &quot;hold&quot; urxvt open"
date: 2011-05-12
forum: General Help
---

### Post by 0nelove on 2011-05-12
Problem with use of -hold|+hold on rxvt-unicode (urxvt) v9.09 on ubuntu server.  On startup, I'm trying to launch terminal apps in urxvt automagically.  E.g: ```
"urxvt -e /usr/bin/weechat-curses +hold"
``` or ```
"urxvt -hold -e mutt"
```
However, -|+hold does not seem to hold the terminal open.  There is a flicker of a new window opening & then it's gone.  
I'm trying to invoke this from .xinitrc (startx-->.xinitrc) and also tried commands from inside awesome wm rc.lua (awful.util.spawn_with_shell("urxvt -hold -e mutt") seem to get same flicker result but closes immediately.

I see this error in .xsession-errors, which might be relevant (do I perhaps need to specify the display??).  Thanks for any help.  
```
[1461:1634:41805904:ERROR:all_status.cc(117)]
Unrecognized Syncer Event: 7                                                                            
E: awesome: a_xcb_io_cb:230: X server connection broke
urxvt: X connection to ':0' broken, unable to recover, exiting.
```

```
rxvt-unicode (urxvt) v9.09 - released: 2010-11-13
options: perl,xft,styles,combining,blink,encodings=eu+vn+jp+jp-ext+kr+zh+zh-ext,fade,transparent,tint,afterimage,XIM,frills,selectionscrolling,wheel,slipwheel,smart-resize,cursorBlink,pointerBlank,scrollbars=plain+rxvt+NeXT+xterm
Usage: urxvt [-help] [--help]
...
 [-n string] [-sl number] [-embed windowid] [-depth number]
 [-/+override-redirect] [-pty-fd fileno] [COLOR="Red"][-/+hold][/COLOR] [-w number] [-b number]
 [-/+bl] [-lsp number] [-letsp number] [-/+sbg] [-mod modifier] [-/+ssc]
 [-/+ssr] [-pe string] [-blt string] [COLOR="red"][-e command arg ...][/COLOR]

```

```
~$ awesome -k
&#10004; Configuration file syntax OK.
```

link to urxvt man: [http://linux.die.net/man/1/urxvt](http://linux.die.net/man/1/urxvt)

---

### Post by TeoBigusGeekus on 2011-05-12
Have you tried adding a sleep command to see if the problem arises from X not having enough time to load?

---

### Post by 0nelove on 2011-05-12
Thanks, now I tried it, but same result.
```
awful.util.spawn_with_shell("sleep 1 && urxvt -hold -e /usr/bin/weechat-curses")
```
I should have clarified that I get this behavior both when rebooting machine and also when simply restarting awesome wm (in which case, I think X is already running).  The .xsession-error might not be related.

---

### Post by TeoBigusGeekus on 2011-05-12
The only thing I can think of is to try with another, less buggy, terminal emulator: xterm comes first to mind.
urxvt might be good, customizable, extensible, etc, but, boy, it's very buggy.

---

### Post by 0nelove on 2011-05-13
Turned out the problem was a conflict in .Xdefaults (conflicting "URxvt*perl-ext-common:" line).  After that fix, "-hold" was actually not necessary to compliment "-e". 

Thanks for the help, TeoBigusGeekus! Appreciated. :KS

---

### Post by tri1976 on 2011-05-24
> **0nelove said:**
> Turned out the problem was a conflict in .Xdefaults (conflicting "URxvt*perl-ext-common:" line).  After that fix, "-hold" was actually not necessary to compliment "-e". 

I have a similar problem and my .Xdefaults contains the following line ```
URxvt.perl-ext-common:  default,matcher,tabbed,clipboard
```How do you fix the problem?  Just remove this line?

---

### Post by 0nelove on 2011-05-24
> **tri1976 said:**
> I have a similar problem and my .Xdefaults contains the following line ```
URxvt.perl-ext-common:  default,matcher,tabbed,clipboard
```How do you fix the problem?  Just remove this line?

What are you trying to accomplish/launch?  Might want to post your .Xdefaults file.

---

### Post by tri1976 on 2011-05-24
I have the following command in my script "urxvt -e $0 &" (basically I just want to run the script in terminal) and the terminal just flash quickly (it doesn't remain open).  Here is my .Xdefaults
```

URxvt.buffered:         true
URxvt.background:       black
URxvt.foreground:       white
URxvt.cursorColor:      green
URxvt.underlineColor:   yellow
URxvt.font:             -misc-fixed-medium-*-*-*-14-*-*-*-*-*-*-*
URxvt.boldFont:         -misc-fixed-bold-*-*-*-14-*-*-*-*-*-*-*
URxvt.perl-ext-common:  default,matcher,tabbed,clipboard
URxvt.urlLauncher:      /home/tri/bin/browser.sh
URxvt.matcher.button:   1
URxvt.scrollBar_right:  true
URxvt.saveLines:        5000
URxvt.transparent:      true
URxvt.shading:          25
URxvt.geometry:         100
URxvt.keysym.C-A-c:     perl:clipboard:copy
URxvt.keysym.C-A-v:     perl:clipboard:paste

```

---

