---
title: "Mouse Problems"
date: 2006-02-27
forum: General Help
---

### Post by Lemurman on 2006-02-27
I'm using a Logitech MX610 wireless mouse with my Gateway laptop and I've recently configured it to acknowledge all of the buttons of the mouse in Linux.  But when I reboot the computer without the usb receiver, it gets stuck at the start-up.  Also, when I have it configured to recognize the buttons, the pointer device in the middle of the keyboard doesn't work.  

Here are the steps I took to configure the mouse, following the instructions provided by endy.

In the terminal:

cat /proc/bus/input/devices
(some of the data here is used later)

Then 
sudo gedit /etc/X11/xorg.conf

I commented out the current mouse data as follows:

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

and copied in the form from endy as follows:

Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        
        Option        "Device"        
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection

I put in the information for "Dev Phys" and "Device" according to the data in the first step and I changed the "Dev Name" to "Logitech USB Receiver", as it is named in the first step.   

Then I saved it and hit Ctrl+Alt+Backspace.  I had to use startx to get back to the Desktop.  The mouse works properly, but I have the prolems with starting up and with the pointer device that I mentioned earlier.  If I leave the section uncommented out and just include the additional section, it doesn't recognize the bottuns as it should.  (The pointer works fine when the section isn't commented out.)

So I was wondering if anyone knew of a way that I could get both the mouse and the pointer to work at the same time and if I can start up the computer without usb receiver inserted.  I'd be happy to provide any more information that is necessary to fix this.

---

