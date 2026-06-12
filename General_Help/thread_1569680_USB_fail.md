---
title: "USB fail"
date: 2010-09-07
forum: General Help
---

### Post by brauer on 2010-09-07
Hi,

This is my first post ):P so please be gentle...

Recently my new (one week old) 64-bit installation of Ubuntu (Lynx) crashed. I had left the machine transfering files from my /home to a network share.

As I came back the mouse was acting a bit weird, small movements of the mouse resulted in the pointer going all over the place and the file transfer hung on an error message - the 1 TB disk only had 1,8 GB left or something similar.
Since I could not close that message via the Ok button i decided to do a Ctrl-Alt-Backspace which also had no effect.

Not wanting to be outdone by a mere desktop machine I Ctrl-Alt-F1:ed into a terminal and did a ```
shutdown -r now
```.

The machine went down without a hitch but would not start again. After inspecting all connections, making sure that nothing was (visibly) fried in the computer etc. I managed to get it to boot without any cables attached. 
I connected the screen cable, the network cable and usb-contacts for mouse and keyboard. I got picture, the machine booted up to the logg in screen but no response on keybord or mouse...

I did a power down via the power button and started again - this time with screen, network and usb connected.

The boot process states that it's initializing usb-controlers but I still have no mouse or keyboard.
I cannot boot from CD since bios requires a keystroke for that.

I have tried all nine available usb-contacts with the same result. 

My question to you is: Should I bother to try and install a usb controller card or should I consider the motherboard fried and try to claim warranty? (The computer is recently bought so warranty should apply).

---

