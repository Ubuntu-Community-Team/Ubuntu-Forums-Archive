---
title: "Monitor issues"
date: 2009-07-14
forum: General Help
---

### Post by Kiwi24 on 2009-07-14
I just downloaded and installed Xubuntu on a Toshiba Tecra 8200 yesterday and it seems to be working great now that I figured out the login issue. My only problem is that the visible screen has about an inch and a half of black all around it. Normally I would press a button on the monitor that would allow me to push the screen out but this laptop has no such function. My next step would have been to go to contorl panel (former windows user) and mess with the monitor attributes there. Does this OS have a control panel? I want to make the screen bigger but have no clue how to go about doing that. I right clicked on the desktop and it shows different resolutions but this in no way seems to affect the visible screen area. I'm stumped. Any solutions? Thanks folks!!

---

### Post by tommcd on 2009-07-15
A quick way to (hopefully) fix this is to boot to recovery mode and choose the option **xfix fix video** (or whatever it says exactly). After running xfix reboot and see if this fixes the problem with the screen not all being used.

To boot to recovery mode, just choose the recovery mode option from the grub menu when you boot Ubuntu. If Ubuntu is the only operating system on the computer then you may not see the grub menu when you bootup. If that is the case, then hit the **Esc** key as the computer boots and you should see the grub menu. Choose recovery mode from the menu.

---

### Post by dbyjazz on 2009-07-15
have you tried changing the resolution settings? And if that doesn't work you can do it in terminal depending on how you want the settings. Just edit your /etc/X11/xorg.conf file to manually specify the virtual screen size:

```
gksudo gedit /etc/X11/xorg.conf
```

Add a block like this to the "Screen" section:

```
Subsection "Display"
    Depth 24
    Modes "1280x800"
    Virtual 1280 800
EndSubsection
```

dunno if that helps!

---

