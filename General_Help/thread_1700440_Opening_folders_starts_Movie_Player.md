---
title: "Opening folders starts Movie Player"
date: 2011-03-05
forum: General Help
---

### Post by JohnMac on 2011-03-05
When I try open my Home/Desktop/Documents/Music folders my Movie Player starts and I get a Gstreamer error message. I only want to start Nautilus!

I am on Maverick now and I had a similar problem (except with Rhythmbox) when I was on Lucid.

Any hints?

My System:

Ubuntu 10.10
GNOME 2.32.0 (Ubuntu 2010-09-27)
Kernal Linux 2.6.35-25-generic
Platform: i686
CPU: AMD 64x2 5200
Memory: 2GB

---

### Post by WorMzy on 2011-03-05
Sounds like you're in a similar situation as the one outlined in this topic: [http://ubuntuforums.org/showthread.php?t=1699253](http://ubuntuforums.org/showthread.php?t=1699253)

The solution is inside.

---

### Post by flipper T on 2011-03-05
i think you are referring to this problem


[http://ubuntuforums.org/showthread.php?t=1659985](http://ubuntuforums.org/showthread.php?t=1659985)

---

### Post by JohnMac on 2011-03-05
Thanks for your prompt reply, that fix did the trick. I have been trying out Tribler, I might give it the flick.

Thanks

John

---

### Post by JohnMac on 2011-03-06
Ops, I spoke too soon. Movie Player no longer starts when I select folders but it does start up when I reboot, with the message "Gstreamer encountered a general stream error"

---

### Post by WorMzy on 2011-03-06
Check the other entries in ~/.local/share/applications/mimeapps.list for anything else that looks out of the ordinary.

---

### Post by JohnMac on 2011-03-07
Nothing odd in this:


[Added Associations]
x-content/audio-player=rhythmbox.desktop;
x-content/audio-cdda=rhythmbox.desktop;
audio/x-aiff=rhythmbox-device.desktop;

:confused:

---

### Post by plucky on 2011-03-07
Should also have ```
inode/directory=nautilus-browser.desktop;
``` to get files opening nautilus.

Good luck

---

### Post by JohnMac on 2011-03-07
I'm sure this makes sense to someone but when I uninstall Movie Player that line of code pops in as such:

[Added Associations]
x-content/audio-player=rhythmbox.desktop;
x-content/audio-cdda=rhythmbox.desktop;
audio/x-aiff=rhythmbox-device.desktop;
inode/directory=nautilus-folder-handler.desktop;

:)

---

