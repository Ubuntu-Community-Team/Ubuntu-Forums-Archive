---
title: "Dell XPS 1530m Display Problem"
date: 2012-10-13
forum: General Help
---

### Post by vandorjw on 2012-10-13
Hey everyone,

I have an older dell laptop. xps 1530m with the nvidia 8400m GS.
The screen on the laptop is broken, but the external display still seems to work.

I have installed Debian Wheezy to it. Grub shows up fine, and I can select either recovery mode or the default option. I then see a whole lot of 

...loading "something" [OK]
After it loads GDM3 (Gnome Display Manager), the external screen turns black. (The primary display is cracked and never displays anything)

I can remote into the laptop via ssh.

UPDATE::
[My Previous Request was for a xorg configuration file that disables the internal LCD]

I am now in the process of making a such a file, but I require some help. This is what I currently have.

> 
[COLOR="DarkSlateBlue"]Section "Monitor"[/COLOR]
    Identifier   "External HDMI"
    Option "Enable" "true"
    Option "PreferredMode" "1920x1080"
EndSection

[COLOR="DarkSlateBlue"]Section "Monitor"[/COLOR]
    Identifier   "Integrated LCD"
    Option "Ignore" "true"
[COLOR="rgb(72, 61, 139)"]EndSection[/COLOR]

[COLOR="DarkSlateBlue"]Section "Device"[/COLOR]
    Identifier         "Card0"
    VendorName         "nVidia Corporation"
    BoardName          "GeForce 8400M GS"
    Driver             "nouveau"
    BusID              "01.00.0"
    Option "Monitor-HDMI1" "External HDMI"
    Option "Monitor-LVDS1" "Integrated LCD"
[COLOR="DarkSlateBlue"]EndSection[/COLOR]

[COLOR="DarkSlateBlue"]Section "Screen"[/COLOR]
    Identifier "screen0"
    Device "Card0"
    Monitor "External HDMI"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection

        SubSection "Display"
                Viewport   0 0
                Depth     32
        EndSubSection

[COLOR="DarkSlateBlue"]EndSection[/COLOR]

[COLOR="DarkSlateBlue"]Section "ServerLayout"[/COLOR]
    Identifier          "layout0"
    Screen              "screen0"
[COLOR="DarkSlateBlue"]EndSection[/COLOR]

[COLOR="DarkSlateBlue"]Section "Files"[/COLOR]
    ModulePath "/usr/lib/xorg/modules"
    FontPath "/usr/share/fonts/X11/misc"
    FontPath "/usr/share/fonts/X11/100dpi"
    FontPath "/usr/share/fonts/X11/75dpi"
    FontPath "/usr/share/fonts/X11/Type1"
    FontPath "built-ins"
[COLOR="DarkSlateBlue"]EndSection[/COLOR]




and this is the error I receive now

```

Fatal server error:
[ 312.888] xf86OpenConsole: Cannot find a free VT

```

---

### Post by papibe on 2012-10-14
Hi cc7gir.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

BTW, your post is marked as SOLVED, you won't get much attention to your problem that way.

---

