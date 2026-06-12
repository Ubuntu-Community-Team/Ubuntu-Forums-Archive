---
title: "Disable Sixaxis as mouse"
date: 2009-08-29
forum: General Help
---

### Post by UtnubuDan on 2009-08-29
I am using my six axis PS3 controller with Mupen64Plus. I have gotten Mupen to recognise the controller and it seems to work. The problem I am having is that the PS3 controller is acting as a mouse in Ubuntu and causing problems moving around when i try to play games. I'm not sure how to disable it as a mouse. I have searched around and tried editing my xorg.conf file, but I seem to crash ubuntu everytime I try to edit it and have to revert back. I'm obviously doing something wrong and need a little help. 

I am using Jaunty 64 bit if that helps. 

It seems like there should be a simple way to do this, I just don't know how.

---

### Post by NoaHall on 2009-08-29
Disconnect the sixaxis controller and run "sudo dpkg-reconfigure -phigh xserver-xorg" from a terminal.

---

### Post by UtnubuDan on 2009-08-29
Am I supposed to do something else beyond that. It looks like it just reverted the conf file to its original form. After I did that I plugged the controller back in. As soon as I pressed the 'PS' button it became a mouse again. 

Here is what my xorg.conf file looks like:


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

