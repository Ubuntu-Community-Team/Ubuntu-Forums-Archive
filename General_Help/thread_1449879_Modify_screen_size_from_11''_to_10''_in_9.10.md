---
title: "Modify screen size from 11'' to 10'' in 9.10"
date: 2010-04-08
forum: General Help
---

### Post by Tilex on 2010-04-08
Hi !

I've installed Ubuntu 9.10 Netbook Remix on my girlfriend's computer, and everything went fine except the computer *thinks* it's got an 11'' monitor when it's actually something like 10.2".

As a result, since Ubuntu windows now relies heavily on the screen size parameters, everything goes "out of the monitor" : browser window, background image, etc ...

In System -> Display, I see it's set as an 11'' monitor...do you know how I can modify this value to be 10'' ?  There used to be an Xorg.conf that one could edit to permanently modify these values but now it's nowhere to be found ...

Thanks !

---

### Post by cogier on 2010-04-08
You will need to create a Xorg.conf file as 9.10 does not use one by default. Follow this link [http://ubuntuforums.org/showthread.php?t=670645]("http://ubuntuforums.org/showthread.php?t=670645")

---

### Post by mcduck on 2010-04-08
> **Tilex said:**
> Hi !

I've installed Ubuntu 9.10 Netbook Remix on my girlfriend's computer, and everything went fine except the computer *thinks* it's got an 11'' monitor when it's actually something like 10.2".

As a result, since Ubuntu windows now relies heavily on the screen size parameters, everything goes "out of the monitor" : browser window, background image, etc ...

In System -> Display, I see it's set as an 11'' monitor...do you know how I can modify this value to be 10'' ?  There used to be an Xorg.conf that one could edit to permanently modify these values but now it's nowhere to be found ...

Thanks !

Whatever physical size Ubuntu recognizes for your monitor is completely irrelevant. It's the _resolution_ that tells how much fits on your screen.

Check what's the correct resolution for your display, and make sure you are using that.

---

### Post by Tilex on 2010-04-08
> **mcduck said:**
> Whatever physical size Ubuntu recognizes for your monitor is completely irrelevant. It's the _resolution_ that tells how much fits on your screen.

Check what's the correct resolution for your display, and make sure you are using that.

Well, the resolution shows 1024x600 and the screen size 11''.

However, from the [computer's specs]("http://techwiki.hardwarecanucks.com/product/2MDIyNA/Samsung-NC10-14GBK/#spec"), the resolution seems OK but the screen size is 10.2", hence what my initial doubt on the screen size.

---

### Post by mcduck on 2010-04-08
> **Tilex said:**
> Well, the resolution shows 1024x600 and the screen size 11''.

However, from the [computer's specs]("http://techwiki.hardwarecanucks.com/product/2MDIyNA/Samsung-NC10-14GBK/#spec"), the resolution seems OK but the screen size is 10.2", hence what my initial doubt on the screen size.

If you are using the correct resolution then there's not really anything you could fix. Many of the programs simply have been designed for higher vertical resolution than the 600 pixels you have, and aren't able to resize to small resolutions.

You can hold down the Alt key to move the windows around from any point in the window (instead of just the titlebar like usually). That will allow you to access those parts of the programs and dialogs that don't fit into the screen.

Also setting a small font size, and perhaps installing some compact theme from gnome-look.org, should give you a bit more space on your screen.

You should probably set the correct DPI value for your display in the advanced font settings (this is really the only thing where display's physical size means anything), but that will only really affect font rendering and text sizes, nothing else. For a 10,2" display with 1024x600 resolution the correct DPI value would be 116

edit: what comes to the background image, you have options to center, tile, zoom or scale the background image in different ways. If the background image isn't the same resolution as your display is, some of the possible settings will stretch or crop the wallpaper.

---

### Post by Tilex on 2010-04-08
Thanks mcduck, I'll try that out tonight :)

---

