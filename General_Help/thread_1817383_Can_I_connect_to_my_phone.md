---
title: "Can I connect to my phone?"
date: 2011-08-03
forum: General Help
---

### Post by boblettoj99 on 2011-08-03
Hi, I have a Samsung Pixon (M8800) mobile phone and would like to be able to get my photos onto the computer. I can get to it from Windows via Samsung's PC Studio but it's such a hassle having to reboot every time!

My phone is present under dev/serial when plugged in via usb cable but it's some weird file that I can't access, is there any way to get to the phone's content?

thanks!

P.S. Running latest version of ubuntu...I think.

---

### Post by SoFl W on 2011-08-03
To find out what version you have type "lsb_release -a" in terminal.  It is important to post the actual version number because 1) It verifies you have the latest version and 2) if someone stumbles across this thread months or a few years from now it lets them compare versions.  "Latest version" means nothing after it is posted.

Is it possible your phone's data is encrypted?  What is the name of the file including the extension?

---

### Post by boblettoj99 on 2011-08-03
Version is 11.04.
Filename is usb-SAMSUNG_Electronics_Co._Ltd._SAMSUNG_Mobile_Modem-if00

I'm not sure exactly of the file type but under properties it says:
Type: Link to character device (inode/chardevice)

It links to: ../../ttyACM0
Which is of type character device. So that's probably the real thing? (It disappears when I unplug the phone)

When I try and open it I get:
/dev/ttyACM0 is not a regular file.
I haven't done any encryption myself, but maybe samsung do?

---

### Post by gandaran on 2011-08-03
does your phone have an option to mount it as usb storage? most phones have that option you just enable when connected to computer then you can transfers files to or from PC.
another way is to install some app on the phone (if the phone  supports apps install) to enable usb storage mount, so if you cant mount the phone there is no way you can get stuff off it.

---

