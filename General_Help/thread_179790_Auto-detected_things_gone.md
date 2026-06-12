---
title: "Auto-detected things gone?"
date: 2006-05-20
forum: General Help
---

### Post by Minn3h on 2006-05-20
I did a dist-upgrade and something went wrong, now things that should automatically work seem to have been unconfigured.  The mouse, the sound, the internet all lost.  I have fixed the internet and gotten the mouse working, partly.  Except I don't know how to configure these things by hand since I have never had to.  My mouse is a logitech mx310 usb mouse and my sound card is:
lspci | grep media
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

How do I fix these things?

---

### Post by Minn3h on 2006-05-20
Fixing the soundcard was as simple as "sudo modprobe snd-intel8x0."  I don't know why my Ubuntu isn't doing these things for me... still stumped about the mouse.

EDIT: Left and right buttons work, middle click works, scroll wheel does not.  Here is the relevant part of xorg.conf:
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option 	   "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
EndSection

---

