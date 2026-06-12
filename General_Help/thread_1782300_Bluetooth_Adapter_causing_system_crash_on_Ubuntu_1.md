---
title: "Bluetooth Adapter causing system crash on Ubuntu 11.04"
date: 2011-06-14
forum: General Help
---

### Post by VinnnyC on 2011-06-14
Hi, and thanks to everyone in advance for their help. This is my first post so if I forgot to give some info let me know. I am using an Acer Aspire 5516-5474 laptop without internal bluetooth. I bought an Azio BTD211 USB bluetooth adapter before installing Ubuntu 11.04. As of now, I can only boot into a 3D enabled desktop(Unity or Ubuntu Classic) with the bluetooth adapter plugged in via a USB hub. Without the adapter plugged in the computer will boot up fine, display the login screen fine, but when trying to load either Unity or Ubuntu Classic I will either get the spinning wheel(the equivalent of Windows hourglass) going on forever, or the desktop will come up but freeze after a few seconds. Either way the mouse still moves, and I can still switch to virtual terminals, though sometimes the mouse cursor also appears on the virtual terminals, but everything on the desktop will be frozen and unresponsive.
       The Desktop will also freeze if the bluetooth adapter is removed after loading the desktop, if you click the bluetooth-applet and then pick "Turn Off Bluetooth", or "sudo kill -2 bluetoothd". After freezing the computer behaves as mentioned above, where I can still move the mouse and switch to virtual terminals.
       The bluetooth adapter needs to be plugged in via the hub. Plugging the adapter in to the laptop via an onboard usb port produces the same behavior as not having the adapter plugged in. The adapter can be switched between the different ports of the hub, as long as it's done before startup.
       This problem only occurs when trying to use one of the 3D desktops, Ubuntu Classic(No Effects) works fine.
       I can't make any sense of this and have tried removing bluetooth-applet from the startup applications list, this produces no different effect. I've also "sudo chmod a-x /etc/init.d/bluetooth", "sudo chmod a-x /usr/sbin/bluetoothd", and have tried removing the "bluez" package, which contains the bluetoothd program. Removing bluez caused the same behavior as not having the bluetooth adapter plugged in(3d desktop failure), even if the adapter was plugged in. I have since undone all the changes I made to try and fix this.
       I really appreciate any help and I'll check back here often to try your recommendations.

P.S. I swapped the CPU(problem occurred before and after swap), so if you think the laptop model is wrong that's why.

---

