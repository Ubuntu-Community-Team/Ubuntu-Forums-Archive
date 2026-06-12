---
title: "Kill a specific window from command line?"
date: 2011-05-07
forum: General Help
---

### Post by TennSeven on 2011-05-07
Hi all,

I have filed bug <a href="https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/777669">777669</a> for Ubuntu 11.04.  Basically, it seems that there is an invisible over everything else in my desktop that is keeping me from clicking on other windows, files, text, etc. that I need to click on.

I think I have identified the offending Window by using xwininfo; is there a way to kill this window using its ID number? Though the window is blocking my clicks it will not respond to alt+F4 or anything like that.

-TennSeven

---

### Post by teachop on 2011-05-07
If you do know the process ID, and want to kill from the command line it is just:

  kill 12345

putting in the right number, if you have permission to do it.

---

### Post by matt_symes on 2011-05-07
Hi

...and as an adjunct to the poster above. To get the process id for a window open a terminal and type

```
xprop
```

The cursor will change to a +. Click in the window required window and in the terminal you will see information about that window. 

Look for the line that says 

```
_NET_WM_PID(CARDINAL) = XXXX
```

XXXX will be the process PID and can be passed into the kill command.

```

matthew@matthew-laptop:~$xprop
<snip>
NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 79691781
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
_NET_WM_USER_TIME(CARDINAL) = 43790622
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
_NET_WM_USER_TIME_WINDOW(WINDOW): **window id # 0x4c00004**
WM_CLIENT_LEADER(WINDOW): window id # 0x4c00001
**_NET_WM_PID(CARDINAL) = 6742**
WM_LOCALE_NAME(STRING) = "en_GB.utf8"
WM_CLIENT_MACHINE(STRING) = "matthew-laptop"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
                program specified location: 0, 0
                program specified minimum size: 284 by 345
                window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "**gcalctool**", "Gcalctool"
WM_ICON_NAME(STRING) = "**Calculator**"
_NET_WM_ICON_NAME(UTF8_STRING) = 0x43, 0x61, 0x6c, 0x63, 0x75, 0x6c, 0x61, 0x74, 0x6f, 0x72
WM_NAME(STRING) = "Calculator"
_NET_WM_NAME(UTF8_STRING) = 0x43, 0x61, 0x6c, 0x63, 0x75, 0x6c, 0x61, 0x74, 0x6f, 0x72
matthew@matthew-laptop:~$ ps aux | grep calc
matthew   **6742**  0.1  0.5 196144 15116 ?        S    21:07   0:00 **gcalctool**
matthew   6775  0.0  0.0   7628   908 pts/4    S+   21:14   0:00 grep --color=auto calc
matthew@matthew-laptop:~$ 
```

Hopefully that will help you out.

Kind regards

---

### Post by idoitprone on 2011-05-07
isnt easier to find the process with
```
ps -a
```

---

### Post by matt_symes on 2011-05-07
Hi

> **idoitprone said:**
> isnt easier to find the process with
```
ps -a
```

That does not give you the window ID but the process ID. The OP said he had the window ID.

Kind regards

---

### Post by AlphaLexman on 2011-05-07
The program / command ```
xkill
```Will change the mouse cursor to an 'X' or a 'skull & crossbones' depending on your settings.
Just click the window you want to kill.

If I remember correctly, in the past, the user had to click on the titlebar in older versions, but now it works by just clicking the window itself.

**NOTE:** This is a moderately dangerous command, use with caution.

Better options are finding the process number (as stated previously) and 'kill #_of_process'. Also use care with the 'killall' command, as it will kill **all** instances of the program, not just the one that is frozen or locked up.

---

### Post by TennSeven on 2011-05-07
Hey guys, none of this works.  xprop just says:

```
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
```

xkill does not kill anything when I click on the affected area (it kills other windows though, so I guess this invisible window I have is just impervious).

Is there no way to tell xorg to kill a specific window ID?

-TennSeven

---

### Post by TennSeven on 2011-05-08
Alright, I got rid of the window though not how I wanted.  I went to the Compiz settings and restored the defaults, which of course re-applied Unity and messed everything else up, and also opened about 10 windows on my screen that were just blank panels.  A reboot of xorg and those invisible windows were no longer blocking my input.

I was able to disable unity and re-enable most of the Compiz stuff I use the most, and the problem has not returned.  If I get some time in the next few days I will try to see if I can narrow the bug down to a specific plugin.

-TennSeven

---

