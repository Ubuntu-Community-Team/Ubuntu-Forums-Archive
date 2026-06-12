---
title: "Broke Unity with Compiz"
date: 2011-07-22
forum: General Help
---

### Post by roololing on 2011-07-22
I was on Ubuntu 11.04 with Unity, and I was fiddling with Compiz. I enabled the shift switcher (or it might have been ring switcher) in the Window Management section, and after 'resolving' some conflicts, the screen went blank.

I pressed CTRL+ALT+F1 and logged in and ran
```
sudo service gdm restart
```
I was then brought to my desktop, but there was no top panel or launcher. I could, however create shortcuts and stuff on the desktop.

I eventually just restarted and ran Ubuntu in classic mode instead, but is there a way I can bring back Unity? I don't really have anything important on Ubuntu (dual-boot with wubi), so recovery isn't a major problem, but it would be nice.

Also, I currently don't have internet at home (just the web browser on my phone), in case that matters.

Any help would be appreciated.

---

### Post by sikander3786 on 2011-07-22
Login to the Unity session, gain access to the tty1 and run unity --reset. It is all explained here.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Later, if you want to enable the cube or just want to enable some animation effects, make sure the plugins listed here are enabled.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by roololing on 2011-07-23
Umm it worked at first, but when I tried to shut down the screen just went black for a couple minutes, so I had to force shut down. When I turned it on and chose to boot Ubuntu, it brought me to GNU Grub. I don't have any idea how this thing works, can I get back to my desktop?

---

### Post by sikander3786 on 2011-07-24
The commands in the above post didn't mean to do anything to the bootloader i.e. Grub. Can't really guess what happened there.

Now to solve this issue, we need you to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Only after you are able to boot the PC successfully, we can again try to repair Unity.

---

### Post by roololing on 2011-07-24
Ah, shoot. It'll be a while before I can do that. But thank you for solving my initial problem.

---

