---
title: "GDM when *poof*"
date: 2006-03-25
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-25
I was following this guide:
[http://ubuntuforums.org/showthread.php?t=75527&highlight=vista-ish](http://ubuntuforums.org/showthread.php?t=75527&highlight=vista-ish)
to make my windows transparent.  It told me to go here:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
to make sure I had the most recent nVidia drivers.  So I followed method 2, and after I have installed some stuff, it said restart.  When my computer rebooted, I saw what looked like a Windows Blue Screen of Death :) and it said x server failed to start.  What did I do!  How do I reconfigure it.  This is everything I did before it broke:
```

sudo gedit /etc/X11/xorg.conf

```
added these lines to the "device" section:
```

        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 

```
```

xcompmgr -cCfF & killall gnome-panel

```
Then went to install nVidia drivers, like this:
```

sudo apt-get install build-essential gcc gcc-3.4
sudo passwd root  ********
uname -r
sudo apt-get install linux-image-386 linux-headers-386

```
Then I restarted and *poof* x-server error message.  Can anyone help?
FYI - I can get to the command prompt, but I am not too comfortable, so please be specific with directions.

---

### Post by trent dillman on 2006-03-25
What does the BSOD say? It might be either of the xorg.conf options.

---

### Post by chocolatetoothpaste on 2006-03-25
[QUOTE=trent dillman]What does the BSOD say? It might be either of the xorg.conf options.[/QUOTE]
BSOD?  Where do I find out what it says?  I have already removed these two lines anyway.
Edit:
Sorry, Blue Screen Of Death.  It is late.
It spits out some os information.  What in particular are you looking for?

---

### Post by chocolatetoothpaste on 2006-03-25
Ok, I found more to the blue screen of death messgage. I looked at the section where it is apparently loading the drivers.  It gives some message about "Default Screen" and then it says it could not load the module "nvidia".  If anyone could help I would sure appreciate it.  I am typing this from lynx right now, and somehow I need to at least get in and burn my pictures, cause I think I need to reinstall.  Or if anyone can tell me how to burn from the command line that would help.  I tried cdrecord and burn, but burn couldn't find my device and cdrecord pretended to burn 3 tracks and then quit.

---

### Post by akiro.yamamoto on 2006-03-25
When you start your system and select Ubuntu in grub.
The system should boot up to the GUI log in screen.
If not you will be given a chance to log in at the console.
So login there then:
```

sudo /etc/init.d/gdm stop (ensure the GUI is stopped)
sudo dpkg-reconfigure -phigh xserver-xorg (reconfigure the Xserver with defaults)
sudo /etc/init.d/gdm start (restart the GUI system)

```
 From this point you should have your GUI system up and running. You can now
try to configure your 3D system and make any changes you need.
Hope this info helps.  ;)

---

### Post by chocolatetoothpaste on 2006-03-25
Wow, thanks, that got me in.  I think I am just going to put dapper on now, though.  Those screen shots are beautiful.  I love the new icons.

---

