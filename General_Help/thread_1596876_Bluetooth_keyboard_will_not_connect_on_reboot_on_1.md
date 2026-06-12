---
title: "Bluetooth keyboard will not connect on reboot on 10.04"
date: 2010-10-14
forum: General Help
---

### Post by rudi246 on 2010-10-14
I have a Rocketfish bluetooth keyboard and mouse combo and am running Ubuntu 10.04. The mouse was easy to set up. I just went to the bluetooth icon and clicked add new device and it connected. The same wasn't true for the keyboard. It gives me the code to type so I typed it and pressed enter and... nothing. So I found a little tutorial and I had to install bluez and type in the terminal, "sudo hidd --search" then enter my password (which I needed to grab my other keyboard to do) and it connected. If I don't use it for a while or reboot, the keyboard will not connect. I have to do the hidd search again which means I need to keep my extra keyboard handy. I had it set up before where it would connect on a reboot, but I got a new hard drive and reinstalled Ubuntu, now I can't remember how I set it up. Could I have set up bluez wrong?

---

### Post by rudi246 on 2010-10-15
I used this tutorial: [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

I did everything it said except I had to edit main.conf instead of hcid.conf. I had read that this version uses main.conf instead of hcid.conf. Then, when it tells me it is connecting, the tutorial says to enter a pin and a window will pop up and I will have to enter the same pin, but that didn't happen. It just connected. Then, it says to do sudo gedit /etc/default/bluez-utils but that file does not exist, gedit just opens a blank page.

Please help, this is really a pain to have to use my old broken keyboard to be able to use my good keyboard.

---

