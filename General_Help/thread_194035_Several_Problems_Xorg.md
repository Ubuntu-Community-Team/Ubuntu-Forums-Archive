---
title: "Several Problems: Xorg?"
date: 2006-06-10
forum: General Help
---

### Post by 18nikko on 2006-06-10
Hi I am having several problems:

1) cntrl+alt+backspace, goes to a login prompt then freezes when trying
to restart X

2) My wacom graphire 4 tablet is very erratic. Right now it
is working fine but sometimes it is not recoginzed. The relevant xorg.config section is pasted below.

3) My kvm switch is not working properly. I have an iogear gcs632U 2-port usb kvm switch. It works fine if I just boot to my linux machine. If I switch to my laptop (WinXP) it works fine, if I switch back the keyboard works fine
but the mouse is dead. I have searched the forum on this one with no luck.
Problem 1 may be related to this??

Any help would be greatly appreciated. I am running Ubuntu 6.06. I have an msi 845PE mother board and a GForce 6600 graphics card I am running the nvidia drivers.

Thanks for any help
Nicholas


Wacom xorg.conf section:

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"          # Change to
    Option         "Device" "/dev/input/event4"        #USB ONLY
    Option         "Type" "stylus"
    Option         "usb" "on"
    Option         "PressCurve" "0,0,100,100"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"          # Change to
   Option        "Device" "/dev/input/event4"        #USB ONLY
    Option         "Type" "eraser"
    Option         "usb" "on"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"          # Change to
    Option         "Device" "/dev/input/event4"        #USB ONLY
    Option         "Type" "cursor"
    Option         "Mode"          "relative"
    Option         "usb" "on"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


:

---

### Post by tseliot on 2006-06-11
[QUOTE=18nikko]Hi I am having several problems:

1) cntrl+alt+backspace, goes to a login prompt then freezes when trying
to restart X[/QUOTE]
Read point 13 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

