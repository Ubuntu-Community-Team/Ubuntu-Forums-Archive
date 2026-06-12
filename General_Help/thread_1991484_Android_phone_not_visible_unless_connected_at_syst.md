---
title: "Android phone not visible unless connected at system startup"
date: 2012-05-30
forum: General Help
---

### Post by Dancso on 2012-05-30
Hey.

I'm developing apps for Android using Eclipse IDE but I've run into a problem trying to set it up on my kubuntu 10.10 system.

I've got everything ironed out from tutorials. I've read the official documentation, I've installed all the necessary stuff, I've set up my rules configuration in udev (I actually read like a dozen of guides for the latter until I found out that it wasn't the thing holding me back)

Basically my problem is, that ADB doesn't even see my device unless it's connected to my PC from system startup. If I do that, ADB sees and even recognizes my device, and I've even managed to use it through Eclipse without any other issues. It's listed through the command "adb devices", and is identified properly.

However, when I disconnect my device from my PC and then reconnect it (or if its not connected before system startup), ADB no longer sees my device.
It's not listed in any way or form when i run "adb devices", not even with a bunch of question marks (as if i hadn't setup the rules properly)

I've found out that the kernel itself does see my device, regardless of when was it connected. (through running lsusb)

Spent hours searching for a solution to no avail. I don't want to restart my system every time I connect my device, but I've absolutely run out of ideas.
Any help would be greatly appreciated!

---

### Post by Dancso on 2012-06-05
Anyone? Please? :(

---

