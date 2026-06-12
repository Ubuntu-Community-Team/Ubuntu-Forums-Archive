---
title: "Attention Nvidia Owners"
date: 2011-05-28
forum: General Help
---

### Post by Shibblet on 2011-05-28
Well, I have had issues with tearing, flicker, frame rate, video playback with VDPAU, compiz and the like.  I think I have finally found a solution for all of us with Nvidia Video Cards.  

This has been tested, and works great on my GTX 260 running Natty, and my Asus 1201n (Ion) running Natty.  I have even tested this at a friends house who has both an Nvidia 8800 and an Nvidia GTX 480.

Open up a terminal, and type:
```
sudo nvidia-settings
```

Then you should get a window that looks like this:
[ATTACH]193467[/ATTACH]

Click on OpenGL settings, and enable Sync to VBlank.  This eliminates tearing from any 3D effects, via Compiz, or VDPAU playback.

Then click on X Server Display Configuration

Adjust your display resolution, and refresh rate to where you want it to be.  In my case, 1680x1050 and 60hz.
[ATTACH]193466[/ATTACH]

Now comes the fun part.  Click on Save X Configuration File.
Then click on Show Preview.
[ATTACH]193469[/ATTACH]

When you get this preview, highlight and copy the text from this window.  Then open a terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

Then, paste your copied text into the new xorg.conf file.
[ATTACH]193470[/ATTACH]

Save your xorg.conf file, and reboot your computer.

This has eliminated any issues for me with Nvidia graphics cards, and Ubuntu.  This works with Kubuntu as well, just use kate instead of gedit.

---

### Post by wildmanne39 on 2011-05-28
> **Shibblet said:**
> Well, I have had issues with tearing, flicker, frame rate, video playback with VDPAU, compiz and the like.  I think I have finally found a solution for all of us with Nvidia Video Cards.  

This has been tested, and works great on my GTX 260 running Natty, and my Asus 1201n (Ion) running Natty.  I have even tested this at a friends house who has both an Nvidia 8800 and an Nvidia GTX 480.

Open up a terminal, and type:
```
sudo nvidia-settings
```

Then you should get a window that looks like this:
[ATTACH]193467[/ATTACH]

Click on OpenGL settings, and enable Sync to VBlank.  This eliminates tearing from any 3D effects, via Compiz, or VDPAU playback.

Then click on X Server Display Configuration

Adjust your display resolution, and refresh rate to where you want it to be.  In my case, 1680x1050 and 60hz.
[ATTACH]193466[/ATTACH]

Now comes the fun part.  Click on Save X Configuration File.
Then click on Show Preview.
[ATTACH]193469[/ATTACH]

When you get this preview, highlight and copy the text from this window.  Then open a terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

Then, paste your copied text into the new xorg.conf file.
[ATTACH]193470[/ATTACH]

Save your xorg.conf file, and reboot your computer.

This has eliminated any issues for me with Nvidia graphics cards, and Ubuntu.  This works with Kubuntu as well, just use kate instead of gedit.

Hi, thank you for the great guide.

---

### Post by LowSky on 2011-05-28
you should use the gksu command over sudo when using gui based programs.

```
gksu nvidia-settings
gksu gedit /etc/X11/xorg.conf
```

---

### Post by mc4man on 2011-05-29
While enabling vsync in nvidia and compiz will certainly help and probably eliminate most tearing those setting are saved in the rc file, not xorg 
(.nvidia-settings-rc, I save in ~/ though I guess you could save in /

---

