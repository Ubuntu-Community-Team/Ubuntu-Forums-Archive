---
title: "Starting Gnome-Terminal on specific workspace"
date: 2010-06-25
forum: General Help
---

### Post by TrotskyIcepick on 2010-06-25
Hi, I am trying to launch gnome-terminal on a specific workspace (4). I have tried the following :

gnome-terminal -t mytitle; wmctrl -r mytitle -t 3

but this just causes the terminal not to launch.

Any ideas how to make this work?

Thanks In Advance
Andrew

---

### Post by lukashjanssen on 2010-06-25
That seems like it should work.... if those commands are run one at a time. You could always just make a batch file with those commands to be able to easily run it.

---

### Post by TrotskyIcepick on 2010-06-25
Nope I'm afraid, even simply gnome-terminal -t Emaild doesn't set the title of the terminal to Emaild.
And after manually changing the title, wmctrl -r Emaild -t 3 does not send the terminal to the expected workspace.

Thanks for the quick response.

---

### Post by VCoolio on 2010-06-25
If you use compiz, check the place plugin; else, give [devilspie](http://foosel.org/linux/devilspie) a try.

---

### Post by TrotskyIcepick on 2010-06-25
Thanks for that, I'll give Devilspie a go. However, for it to work, it needs a window title. I thought the option to set a gnome-terminal window title was to add -t windowtitle to the gnome-terminal command, but this appears not to be the case. I have also tried --title option to gnome-terminal and this doesn't work either.

Any ideas?

---

### Post by VCoolio on 2010-06-25
I don't know why gnome-terminal doesn't listen to the title option; try rxvt-unicode, it's a better terminal anyway, or roxterm. But devilspie doesn't necessarily need a title, you can use class or name also (but then it will affect all instances of gnome-terminal). Use xprop to find out about window properties (run xprop, then click the window and read the output).

---

### Post by gmargo on 2010-06-25
> **TrotskyIcepick said:**
> gnome-terminal -t Emaild doesn't set the title of the terminal to Emaild.

That works fine for me.  Is there any chance that you are actually executing **/usr/bin/gnome-terminal.wrapper** (which does not support the -t option)?

---

### Post by lukashjanssen on 2010-06-26
Yes, ```
gnome-terminal -t mytitle
``` definitely works on my machine...

What does the terminal output when you try to run that?

---

### Post by TrotskyIcepick on 2010-06-28
I'm definitely running gnome-terminal not gnome-terminal.wrapper. When run with the -t option no output is produced. If I run xprop on the window it gives me : 

_NET_WM_ICON_GEOMETRY(CARDINAL) = 1190, 942, 1, 1
_COMPIZ_WM_WINDOW_BLUR_DECOR(INTEGER) = 4, 0, 5, 4, -23, 6, -4, -22, 5, 2, -22, 6, -2, -21, 5, 1, -21, 6, -1, -20, 5, 0, -20, 6, 0, -18, 5, -1, -18, 6, 1, 0, 9, 0, 0, 10, 0, 2, 9, 1, 2, 10, -1, 3, 9, 2, 3, 10, -2, 4, 9, 4, 4, 10, -4, 5, 5, -1, 0, 9, 0, 0, 6, 0, 0, 10, 1, 0
_COMPIZ_WINDOW_DECOR(INTEGER) = 20080529, 42003256, 1, 1, 23, 5, 0, 0, 23, 0, 26, 0, 589925, -9, -31, -6, 0, 769, 32767, 0, 0, 524389, 760, -31, -6, 0, 32767, 32767, 769, 0, 590182, -6, -31, 11, 0, 17, 32767, 787, 0, 395413, -9, 0, 0, -169, 32767, 169, 1, 33, 264341, -9, 169, 0, -169, 32767, 32767, 170, 33, 395929, -9, -169, 0, 0, 32767, 169, 340, 33, 395430, 0, 0, 11, -169, 32767, 169, 342, 33, 264358, 0, 169, 11, -169, 32767, 32767, 511, 33, 395946, 0, -169, 11, 0, 32767, 169, 681, 33, 589993, -9, 0, -383, 15, 392, 32767, 0, 46, 524457, 383, 0, -383, 15, 32767, 32767, 392, 46, 590250, -383, 0, 11, 15, 394, 32767, 787, 46
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
        window state: Normal
        icon window: 0x0
_NET_WM_DESKTOP(CARDINAL) = 0
_NET_WM_STATE(ATOM) = 
_NET_FRAME_EXTENTS(CARDINAL) = 1, 1, 23, 5
_NET_FRAME_WINDOW(WINDOW): window id # 0x1f2b0fc
WM_HINTS(WM_HINTS):
        Client accepts input or input focus: True
        Initial state is Normal State.
        bitmap id # to use for icon: 0x2e00024
        bitmap id # of mask for icon: 0x2e00027
        window id # of group leader: 0x2e00001
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x10, 0x0, 0x0, 0x0

(a few icon details)

WM_WINDOW_ROLE(STRING) = "gnome-terminal-window-2735-401635614-1277713015"
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 48268943
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
_NET_WM_USER_TIME(CARDINAL) = 251031452
_NET_WM_USER_TIME_WINDOW(WINDOW): window id # 0x2e0868e
WM_CLIENT_LEADER(WINDOW): window id # 0x2e00001
_NET_WM_PID(CARDINAL) = 2735
WM_LOCALE_NAME(STRING) = "en_GB.utf8"
WM_CLIENT_MACHINE(STRING) = "andy-pc"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
        program specified minimum size: 41 by 53
        program specified resize increment: 6 by 13
        program specified base size: 17 by 27
        window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "gnome-terminal", "Gnome-terminal"
WM_ICON_NAME(STRING) = "andrew@andy-pc: /usr/bin"
_NET_WM_ICON_NAME(UTF8_STRING) = 0x61, 0x6e, 0x64, 0x72, 0x65, 0x77, 0x40, 0x61, 0x6e, 0x64, 0x79, 0x2d, 0x70, 0x63, 0x3a, 0x20, 0x2f, 0x75, 0x73, 0x72, 0x2f, 0x62, 0x69, 0x6e
WM_NAME(STRING) = "andrew@andy-pc: /usr/bin"
_NET_WM_NAME(UTF8_STRING) = 0x61, 0x6e, 0x64, 0x72, 0x65, 0x77, 0x40, 0x61, 0x6e, 0x64, 0x79, 0x2d, 0x70, 0x63, 0x3a, 0x20, 0x2f, 0x75, 0x73, 0x72, 0x2f, 0x62, 0x69, 0x6e

That is on a window run with the -t option set. The version of gnome-terminal is 2.29.6. Running rxvt-unicode with the -title option doesn't work either.

Thanks again
Andrew

---

### Post by gmargo on 2010-06-28
> **TrotskyIcepick said:**
> 
WM_NAME(STRING) = "andrew@andy-pc: /usr/bin"


The default bash shell prompt (given by the $PS1 variable) overwrites the terminal title string with "user@machine: current-directory".  If you still use this default $PS1, then your title given with the -t option is overwritten when the shell gives it's first prompt. So to make -t work, you have to change the PS1 in your $HOME/.bashrc.

Here's the offending bit from the default .bashrc:
```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="**\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]**$PS1"
    ;;
*)
    ;;
esac

```

---

### Post by TrotskyIcepick on 2010-06-30
Thanks gmargo, commenting out the relevent section of .bashrc causes -t option to work.

Now, back to my original issue, sending the gnome-terminal to a specific workspace. This is what I've tried:

gnome-terminal -t mytitle; wmctrl -r mytitle -t 3

However,this does absolutely nothing. The options are correct as verified by wmctrl --help.

Any ideas?

Thanks In Advance
Andrew

---

### Post by gmargo on 2010-06-30
Our idea of "workspace" is not the same as wmctrl's idea of "desktop".

Even though I have four "workspaces" configured, wmctrl shows only one "desktop".  Use the -d option to list the desktops:
```

$ wmctrl -d
0  * DG: 5464x768  VP: 0,0  WA: 0,24 1366x720  Desk 1

```My "workspaces" show up as "viewports" on a single really-wide "desktop".  Therefore I cannot use the -t option to switch desktops, since I have only one.  However, I was able to use the -e option to move a window to another "workspace", by adding the width of a "viewport" onto it's starting column.  Something like this:
```

wmctrl -F -r 'Target' -e 0,2002,-1,-1,-1

```

---

### Post by TrotskyIcepick on 2010-07-02
Thanks for that Gmargo, it worked a treat.

Regards
Andrew

Well, at least it works if you enter the command at the command line. However, if you are running it as a launcher on Cairo dock for example (as I am) it just opens the terminal window on the current workspace, almost as though it's not executing the wmctrl part of the command.

The exact command I'm trying to run is gnome-terminal -t "Emaild";wmctrl  -F -r 'Fred' -e 0,5760,-1,-1,-1.

Slight departure from the original question, if I want this terminal to run ./sshlogin.sh xxx.xxx.xxx.xxx once opened how do I do that?

---

### Post by gmargo on 2010-07-02
> **TrotskyIcepick said:**
> 
The exact command I'm trying to run is gnome-terminal -t "Emaild";wmctrl  -F -r 'Fred' -e 0,5760,-1,-1,-1.

The "Emaild" and "Fred" strings should be the same string.  Is that a typo?

---

### Post by TrotskyIcepick on 2010-07-05
> **gmargo said:**
> The "Emaild" and "Fred" strings should be the same string.  Is that a typo?

Oops, yes that is indeed a typo ;)

The actual command I'm running is correct though, that was just a typo when I posted here.

---

### Post by Lewis Cowles on 2010-08-12
Hi, when using the -e flag (because my gnome has one massive desktop which it pages) is it possible to simply re-position the desktop to switch to another window and then launch an app?

---

