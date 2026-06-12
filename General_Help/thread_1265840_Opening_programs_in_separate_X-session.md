---
title: "Opening programs in separate X-session"
date: 2009-09-13
forum: General Help
---

### Post by GammaPoint on 2009-09-13
I've got a two separate X sessions configured (one for my monitor, the other for my TV). If I bring my mouse over to my TV (the 2nd x-session) and open up a program (say gThumb) from the drop down menu it opens up on the monitor instead of the TV. Why is this? And can I do anything about it?

Thanks for your help!

---

### Post by thegreatsnafu on 2009-09-13
Hi,

This is probably because you set the monitor as your main display. You are going to have to figure out how to change it to your TV for I don't know how. Sorry... :(

---

### Post by GammaPoint on 2009-09-14
> **thegreatsnafu said:**
> Hi,

This is probably because you set the monitor as your main display. You are going to have to figure out how to change it to your TV for I don't know how. Sorry... :(

Well my monitor is certainly my main display most of the time. Sometimes I want to do something on the TV though. I was hoping that there was a way to open programs on the TV without rearranging my X sessions or something that would require an X restart.

---

### Post by unutbu on 2009-09-14
When you say you have two separate X-sessions running,
are they different sessions in the sense that you can flip between them by
pressing Ctrl-Alt-F* keys?

Or do you have TwinView or Xinerama set up so you have one workspace with a giant resolution spanning two monitors?

Also, what window manager do you use?

---

### Post by GammaPoint on 2009-09-14
> **unutbu said:**
> When you say you have two separate X-sessions running,
are they different sessions in the sense that you can flip between them by
pressing Ctrl-Alt-F* keys?

I don't know how to flip between them with Ctrl-Alt-F* (F* standing for the various function keys I guess?).  I have separate X sessions in the sense that if I open nvidia-settings and look under 'X server display configuration' it says 'configuration: separate X screen'. 'Twinview' is the other option that I'm not using. Xinerama is not clicked either. To go from one screen to the other I simply drag my mouse over to the right and it goes to the second X session (however, they're not connected in the sense that I can't drag, e.g., a browser window over to the second session. Doing this just makes the browser window rotate on the compiz cube on my monitor). 

I'm using Emerald with Compiz I believe. Gnome desktop manager.

---

### Post by unutbu on 2009-09-14
GammaPoint, can you open 2 terminals (Applications>Accessories>Terminal), one on each screen? If so, please run
```

xwininfo       # then click on the terminal
echo $DISPLAY
```

on both terminals and post the output.

---

### Post by GammaPoint on 2009-09-14
Okay, output from my monitor:

```

bmalone@papabear:~$ xwininfo

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x4a63e17 "bmalone@papabear: ~"

  Absolute upper-left X:  5
  Absolute upper-left Y:  47
  Relative upper-left X:  5
  Relative upper-left Y:  47
  Width: 657
  Height: 435
  Depth: 32
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x4a00005 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +5+47  -618+47  -618-542  +5-542
  -geometry 80x24+5+47

bmalone@papabear:~$ echo $DISPLAY
:0.0


```

and from the TV

```

bmalone@papabear:~$ xwininfo

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x4e00006 "bmalone@papabear: ~"

  Absolute upper-left X:  5
  Absolute upper-left Y:  47
  Relative upper-left X:  5
  Relative upper-left Y:  47
  Width: 657
  Height: 435
  Depth: 32
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x4e00005 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +5+47  -698+47  -698-286  +5-286
  -geometry 80x24+5+47

bmalone@papabear:~$ echo $DISPLAY
:0.1

```

Thanks :)

---

### Post by unutbu on 2009-09-14
GammaPoint, I do not have two monitors to test my suggestions, so there is a good chance none of this will work. But for what it's worth, perhaps try this:

Open a terminal on the TV and type
```

DISPLAY=:0.1 gthumb
```

If that opens a gthumb window on the TV, then we are in business.
You can then go to System>Pref>"Main Menu" and add a new menu item for "gThumb (TV)"
and use as its the command  "DISPLAY=:0.1 gthumb".

---

### Post by GammaPoint on 2009-09-14
> **unutbu said:**
> GammaPoint, I do not have two monitors to test my suggestions, so there is a good chance none of this will work. But for what it's worth, perhaps try this:

Open a terminal on the TV and type
```

DISPLAY=:0.1 gthumb
```

If that opens a gthumb window on the TV, then we are in business.
You can then go to System>Pref>"Main Menu" and add a new menu item for "gThumb (TV)"
and use as its the command  "DISPLAY=:0.1 gthumb".

Yes, that works! A little embarassing that I didn't think of trying that myself since I use the 'DISPLAY=:0.1' option all the time to run mplayer on the TV but that's great. I didn't know how to add options to the menu (or to figure out what terminal command corresponded to the menu options) so your last suggestion helps me with both of those. Thanks for your help! I appreciate it!

---

