---
title: "internet not working after 10.04 install"
date: 2010-10-01
forum: General Help
---

### Post by Dex73 on 2010-10-01
Hi. I have a "hp Pavilion Entertainment PC" and I just put 10.04 on it and the internet won't work. It has a separate button that you touch not click or push that lights up red when off and blue when on. It's currently stuck on red and will not connect with my wireless net work. This laptop is used by my family and my personal laptop is working fine. I took a picture of the screen after install and it shows errors. I need step by step help on this one. I have the picture I took with my camera. It was black with reflections and I use gimp to help it look better. Don't be alarm with the background. The problem is that it is 2420x1044 pixels. Can someone help me fix this so I can give you all the info.

---

### Post by slooksterpsv on 2010-10-01
At the top, see where it shows the date and time, and there's a wireless icon (it may have a red x or an exclamation mark on it). Right-click on that and see if networking is enabled.

Can you post the screenshot to like imageshack or even zip it and post it here?

---

### Post by Dex73 on 2010-10-01
It's enabled. Sorry for any confusion, I'm not talking about the screen. The button I mentioned is on the keyboard. I figured out how to reduce the pixels so now I can show you the picture of the errors after install. Is this related?

---

### Post by slooksterpsv on 2010-10-01
> **Dex73 said:**
> It's enabled. Sorry for any confusion, I'm not talking about the screen. The button I mentioned is on the keyboard. I figured out how to reduce the pixels so now I can show you the picture of the errors after install. Is this related?

You're good, no confusion in my opinion; the errors your seeing is related to the wireless, it looks like you don't have the drivers needed for the broadcom chipsest... let me see if I can help you out and find what drivers you need or where to get them....

[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146) - that's an excellent guide for getting the broadcom drivers to work. Let me know if you get stuck or need help with specific instructions.

---

### Post by Dex73 on 2010-10-02
Couldn't get the guide you recommended to work, but update manager had my back once I plugged in an Ethernet cable. After reboot firmware files were installed on start up. Wireless now works and I've moved on to get it to play music and movies. Says it needs 3 gstreammer packages. Internet vids seem to be fine though thanks for the help. I think all start a new thread about the gstreammer problem if I can't resolve it.

---

### Post by slooksterpsv on 2010-10-02
> **Dex73 said:**
> Couldn't get the guide you recommended to work, but update manager had my back once I plugged in an Ethernet cable. After reboot firmware files were installed on start up. Wireless now works and I've moved on to get it to play music and movies. Says it needs 3 gstreammer packages. Internet vids seem to be fine though thanks for the help. I think all start a new thread about the gstreammer problem if I can't resolve it.

That's good the wireless is working; as for the gstreamer packages, install ubuntu-restricted-extras - to get some of them, if that doesn't resolve the issue completely, look up gstreamer in Software Center, I believe it's the ugly package, checking... yeah gstreamer extra plugins - it's the ugly package. Install that and it should get your music up and working =D

---

### Post by Dex73 on 2010-10-02
I was able to fix it with synaptic before you posted, but thanks for the advice anyway. That computer is running smooth now.

---

