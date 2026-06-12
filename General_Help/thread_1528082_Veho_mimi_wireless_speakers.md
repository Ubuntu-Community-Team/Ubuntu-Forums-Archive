---
title: "Veho mimi wireless speakers"
date: 2010-07-10
forum: General Help
---

### Post by Elliotal on 2010-07-10
HI there, i just purchased some Veho Mimi wireless speakers. It comes with a usb adapter which sends out the wireless signal to the speakers.

When using windows vista the usb is recognised and everything works fine. However when i try and use it on Ubuntu, nothing works at all.
Any ideas?

Cheers

---

### Post by lluis.geophysic on 2010-07-28
Hi,

I had the same problem. The fix is in this post:

[http://ubuntuforums.org/showthread.php?t=1028641](http://ubuntuforums.org/showthread.php?t=1028641)

1-You have to install pulseaudio volume control:

sudo apt-get install pavumeter
2- Start the application that you want to output to the wifi speaker

3- Go to Applications>Sound & Video>PulseAudio Volume control

4- In the Playback tab, click on the downgoing at the right of your listed application, and select "Move Stream...". That gives me two options, click in the "Wireless Audio - USB Audio" and tadaaa!

You can make it the default output device in the "Output Devices" tab.

Hope it helps

---

### Post by scholzilla on 2011-12-14
this fix is apparently no longer applicable. Does someone have an update?

---

