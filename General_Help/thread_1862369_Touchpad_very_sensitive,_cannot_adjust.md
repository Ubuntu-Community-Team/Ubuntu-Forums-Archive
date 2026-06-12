---
title: "Touchpad very sensitive, cannot adjust"
date: 2011-10-16
forum: General Help
---

### Post by CaKiwi on 2011-10-16
The touchpad on my Toshiba C655 laptop is very sensitive. I installed Gpointing device application but when I run it the touchpad shows up as a mouse so I don't see the fields to adjust. If I plug in a mouse it shows up as another mouse. Gpointing devices sees the touchpad correctly on a different model of Toshiba laptop.

Any help greatly appreciated

---

### Post by CaKiwi on 2011-10-17
Here's a screenshot of how my touchpad shows up in GPointing Device Settings.


EDIT: Here's some more info. When I enter
```
$ synclient -l
```
I get
```
Couldn't find synaptics properties. No synaptics driver loaded?
```
I tried to install synaptics with the following result
```
$ sudo apt-get install xserver-xorg-input-synaptics
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``` I assume all this means the touchpad is not being recognized by the kernel. How do I rectify this?

---

