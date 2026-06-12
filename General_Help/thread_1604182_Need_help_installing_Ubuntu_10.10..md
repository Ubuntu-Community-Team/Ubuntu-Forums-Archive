---
title: "Need help installing Ubuntu 10.10."
date: 2010-10-23
forum: General Help
---

### Post by Kyle2071 on 2010-10-23
Hey, let me start my saying that I'm a total Ubuntu novice. I briefly messed around with it with an old desktop that I no longer have, and that's about it. Anyways, I saw that there was a new version of the netbook version of Ubuntu 10.10, so I thought I'd try it on my laptop, which is a newer Toshiba Satellite. I tried to install it using the USB method that main website tells you to use, but I ran into a problem. After restarting and booting with the USB drive, Ubuntu would begin to load up, but then would suddenly stop and say that is unable to find medium with live file system. Then it just left me stuck there with no way to exit or restart, so I just pulled the battery out. Can anyone help me figure this out? Any help would be greatly appreciated!

---

### Post by iammagicboy on 2010-10-23
Have you try wubi?Boot your laptop into windows ,then insert your usb.Open the wubi.exe in the usb and try it.
I'm not sure that netbook remix can run in laptop
I recommend to use the desktop version
Get it here:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by sikander3786 on 2010-10-23
I wouldn't recommend a Wubi install since it is slower than a regular one and seems to be a bit problematic in some cases.

First of all check the MD5SUM of the downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then use either unetbootin to create a USB,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or follow instructions on this page,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

