---
title: "i3 wm, help to set the traybar"
date: 2012-01-31
forum: General Help
---

### Post by working_egg on 2012-01-31
I want to try i3 wm, but unfortunately unable to properly config the traybar. 
As I understood from their page, one should add the following lines to ~/.i3/config to let tray work

bar {
    output            LVDS1
    status_command    i3status
    position          top
    mode              hide
    workspace_buttons yes
    tray_output       HDMI2
    
    font -misc-fixed-medium-r-normal--13-120-75-75-C-70-iso10646-1

    colors {
        background #000000
        statusline #ffffff

        focused_workspace  #ffffff #285577
        active_workspace   #ffffff #333333
        inactive_workspace #888888 #222222
        urgent_workspace   #ffffff #900000
    }
}

I use a monitor connected to the laptop, so " tray_output       HDMI2".

But as soon as I get logged into i3 session via gdm, I'm brought back to the login screen again, as if i3 is unable to start and crashes. When I delete bar {...} paragraph from the ~/.i3/config file, all is ok. 

How do you set up status bar and tray in i3, guys?

---

### Post by lechien73 on 2012-01-31
Are you sure your monitor is on HDMI2? For example, if you have your monitors connected and then, from the terminal, run:

```
xrandr
```

Does this show HDMI2 as a valid output? On my laptop, the big monitor would be HDMI1.

---

### Post by working_egg on 2012-01-31
> **lechien73 said:**
> Are you sure your monitor is on HDMI2? For example, if you have your monitors connected and then, from the terminal, run:

```
xrandr
```

Does this show HDMI2 as a valid output? On my laptop, the big monitor would be HDMI1.

Not sure really, I'm not even sure if HDMI2 is the proper name for my dell monitor interface.
Whenever I launch openbox session, I disable the laptop monitor with nvidia-settings app, so I have only one monitor working. How does this mess with the i3bar config settings is the next question.
xrandr output is:
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 2560 x 1024

---

### Post by lechien73 on 2012-01-31
Is that all it reports? Are you connecting the external monitor via HDMI, or is it a regular VGA cable?

If it's regular VGA, then try changing HDMI2 to VGA1 in the config file.

---

### Post by working_egg on 2012-02-01
VGA cable it is, I will, but that will not solve my issue of i3 wm chashing after login. Did anybody use i3 here?

---

### Post by bruno.braga on 2012-07-16
> **working_egg said:**
> VGA cable it is, I will, but that will not solve my issue of i3 wm chashing after login. Did anybody use i3 here?

Maybe too late for this thread, but i3 people have launched a FAQ recently... it might be a good idea to check it out there...

[http://faq.i3wm.org](http://faq.i3wm.org)

---

