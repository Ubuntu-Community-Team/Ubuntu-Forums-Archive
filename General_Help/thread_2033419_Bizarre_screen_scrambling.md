---
title: "Bizarre screen scrambling"
date: 2012-07-26
forum: General Help
---

### Post by timswait on 2012-07-26
I have Kubuntu 12.04 installed on a Dell Precision laptop, and nVidia Quadro 2000M graphics.
I was trying to get OpenGL working on it, but now the screen is bizarrely scrambled! I started by trying to open nVidia settings, but it cxame up with a error when I opened it telling me to run "nvidia-xconfig" I did that from terminal, it gave a warning that there was no x configuration file found, and it had created a new xorg.conf. When I rebooted I found I only had 640x480 resolution and the screen was flipped vertically. Reading around I found that Kubuntu no longer uses xorg, so I deleted the xorg file from the /etc/X11 folder. This has now restored the resolution, but I still have the vertical mirror image problem. I get a normal log in screen into which I enter my user name and password. The splash screen initially displays correctly but then half way through it flips vertically! From then on the screen is a strange mixture of upside down and the right way up. All the items are in the right place, but each item is flipped vertically. The toolbars etc are all where I would expect them, but are all vertical mirror images. If I open a window the title bar is correct(and on the top), but all the content is vertically flipped. When I click the mouse I need to click where things should be if the screen was normal, not where they actually are! This makes it nearly impossible to do anything with it, although I can open terminal and type commands. is there anything I can do to restore everything back to default? I tried running from a live CD (which works fine) and copying the whole X11 folder from the live CD root/etc folder into my hard-drive root/etc folder, but this hasn't changed anything.

---

### Post by timswait on 2012-07-26
[https://docs.google.com/open?id=0B4U35RciYQ9kMGxkdW16WDZVOEk]("https://docs.google.com/open?id=0B4U35RciYQ9kMGxkdW16WDZVOEk")
Uploaded an image of the screen here. BTW the main panel is supposed to be across the top of the screen, as I say, each item is in the right place, the mouse moves correctly (ie push it away from me it moves up), but each item is flipped.

---

### Post by timswait on 2012-07-26
I've just found this bug report, which seems to describe my symptoms exactly:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/809583]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/809583")
The bug report says the problem is solved, but I'm running 12.04, and am getting exactly this problem He mentions disabling compositing from the command line, does anyone know what this command is? Navigating menus is virtually impossible, and I don't even know what compositing is or where the settings are as I've never knowingly enabled it.
This thread also shows the same symptoms, but no solutions :(
[http://ubuntuforums.org/showthread.php?t=1613115]("http://ubuntuforums.org/showthread.php?t=1613115")

---

### Post by timswait on 2012-07-26
Seem to have cured it. Alt+Shift+F12 disabled desktop effects, and unflipped everything. I then changed the engine to Xrender from OpenGL and it seems fine :) I guess the problem is something to do with my OpenGL then.

---

