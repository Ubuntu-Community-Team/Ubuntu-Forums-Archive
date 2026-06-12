---
title: "ATI RS200/RS200M [IGP 340M] problem."
date: 2009-12-18
forum: General Help
---

### Post by JunkieMKD on 2009-12-18
I have HP Compaq Laptop with this specifications

Procesor:Intel(R) Pentium(R) 4 CPU 2.40GHz
Memory:512mb
GraphicCard: ATI Radeon IGP 340m
OS:Ubuntu Linux 9.10

For first time i installed Linux,and i have problems with graphic.When visual effects are on normal i can`t normaly work :( windows are freezing.I changed visual effects on none and everythings fine but i can`t see notifications and some programs.I get this...

[IMG]http://i.imagehost.org/0258/Screenshot.jpg[/IMG]

[IMG]http://i.imagehost.org/0536/Screenshot-1.jpg[/IMG]

so i tried many times to fix this but i can`t.Is there anyway to fix this?Im new with linux i know little bit.

Thanks

JunkieMKD

---

### Post by dcstar on 2009-12-18
> **JunkieMKD said:**
> I have HP Compaq Laptop with this specifications

Procesor:Intel(R) Pentium(R) 4 CPU 2.40GHz
Memory:512mb
GraphicCard: ATI Radeon IGP 340m
OS:Ubuntu Linux 9.10

For first time i installed Linux,and i have problems with graphic.When visual effects are on normal i can`t normaly work :( windows are freezing.I changed visual effects on none and everythings fine but i can`t see notifications and some programs.I get this...
.........
so i tried many times to fix this but i can`t.Is there anyway to fix this?Im new with linux i know little bit.

Thanks

JunkieMKD

Install and run the **envy** packages to get the latest video drivers.

---

### Post by JunkieMKD on 2009-12-19
> **dcstar said:**
> Install and run the **envy** packages to get the latest video drivers.

I tried but it says no recommended drivers :(

---

### Post by al_rix on 2010-01-10
I had similar issues on a Thinkpad R40e - fixed it by adding following lines to device section in /etc/X11/xorg.conf :

Section "Device"
    Identifier "ATI Technologies Inc R200"
    Driver "radeon"
    Option "AccelMethod" "XAA" 
    Option "RenderAccel" "Off"
#    Option "AGPMode" "4" 
#    Option "EnablePageFlip" "On"
EndSection

(If you don't have an /etc/X11/xorg.conf just add this to a new file). With these options you won't get good 3d performance but notifications etc. all work fine and CPU load by Xorg is a normal level.

---

### Post by dcstar on 2010-01-11
For **very** old ATI video chipsets:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

