---
title: "Change resolution permanently of second monitor"
date: 2011-04-13
forum: General Help
---

### Post by TMachado on 2011-04-13
I use a laptop and Ubuntu 10.10 x86. Problem is I have a second monitor with 1280x1024 native resolution, and that resolution is not displayed in modes.

So I solved my problem temporarily using this:

```
xrandr --newmode &#8221;1280x1024_60.00&#8221; 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA1 &#8220;1280x1024_60.00&#8221;
```

The 1280x1024 mode appears and I do "apply" -> all OK. And then I press "make default" (where I get a pop screen confirmation warning me that will be the default config after reboot) - nice!

Problem is: "make default" don't work! And I have to add a new mode after each login. 

Anyone knows how can I solve my problem?

---

### Post by searchfgold6789 on 2011-04-13
I would make those two commands into a bash script and [make it into a script to be run at startup.]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

---

### Post by TMachado on 2011-04-13
> **searchfgold6789 said:**
> I would make those two commands into a bash script and [make it into a script to be run at startup.]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

I did that unfortunately do not work. My second monitor before login is connected with different resolution, and after resolution is disconected, and if I turn it on, the resolution is not available.

---

### Post by stoneage on 2011-04-13
If you have an nVidia graphics card use nVidia X Server settings to 'Save to X Configuration File'

This will create a file you can use and edit as an xorg.conf

The alternative is to write the settings you create with xrandr as a modeline, and again, save as an xorg.conf file.

More help here:-
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

