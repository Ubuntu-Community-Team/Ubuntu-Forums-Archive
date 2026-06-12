---
title: "Just got a new keyboard, GRUB2 cant see it"
date: 2012-04-14
forum: General Help
---

### Post by wobbles-grogan on 2012-04-14
Hi all,

I know theres a few threads on this already, but none of them solve my problem.

My setup is as follows:
Asus P8P67 Mobo
Corsair Vengance K60 USB keyboard
Dual booting between windows7 and Kubuntu 11.10.

The problem is my bios can see the keyboard. I can use the keyboard right up until the point GRUB2 loads. I can use the keyboard in the OS (I'm typing this on it now...), but the keyboard simply will not work in the GRUB2 menu. I have tried all combinations of settings with legacy usb support etc and nothing works.

The weird thing is, I have another usb keyboard (a logitech) that works no problem with grub, and thats how I've been switching between OS's, but I shouldn't need to have another keyboard plugged in just for the GRUB menu.. 

Can anyone point me in the right direction here?! 
I'm getting desperate....

Cheers!

---

### Post by oldfred on 2012-04-14
Welcome to the forums.

Are both keyboards USB? 

I had the same issue but the new keyboard was USB and the old PS/2 one worked. It was a BIOS setting to turn on USB ports for mouse & keyboard. 

It seems both Windows & Ubuntu use their own drivers but grub is using BIOS settings.

---

### Post by wobbles-grogan on 2012-04-15
Yeah, it's USB too. Both are USB, and both work the same in the bios.
It's just grub that can't see my new keyboard...

---

### Post by oldfred on 2012-04-15
Using the same port? Not a newer uSB3 port?

It should work as I understand it. A USB keyboard should be a USB keyboard.

---

### Post by wobbles-grogan on 2012-04-16
> **oldfred said:**
> Using the same port? Not a newer uSB3 port?

It should work as I understand it. A USB keyboard should be a USB keyboard.

Thats what I thought too, but apparantly not!

I've tried the keyboard in all the ports at this stage, the old logitech works in em all (including the USB3 ports). 

Im beginning to think its something to do with the USB hub thats built into the keyboard, I ahve a sneaking suspicion that its messing GRUB up.

I'm resigning to the fact ill have to have the old keyboard plugged in so I can select which OS to boot to, and use the new one for my typing needs. Not ideal but I'll go with it...

---

### Post by dcstar on 2012-04-17
> **wobbles-grogan said:**
> Hi all,

I know theres a few threads on this already, but none of them solve my problem.

My setup is as follows:
Asus P8P67 Mobo
Corsair Vengance K60 USB keyboard
Dual booting between windows7 and Kubuntu 11.10.
.........

Do you have an internal memory card reader plugged into a USB connector on the MB?

I have seen posts where unplugging this hardware can make a difference.

---

### Post by wobbles-grogan on 2012-04-17
> **dcstar said:**
> Do you have an internal memory card reader plugged into a USB connector on the MB?

I have seen posts where unplugging this hardware can make a difference.

I dont, no. I do have a WiFi dongle though...

Ill try unplugging everything else today to see if that makes a difference. Im hoping it wont, as I wouldnt regard it as a fix. Although, I guess i could look at the boot log (if there is on) and see what different driver is being loaded when the keyboard is in on its own, compared to when everything else is plugged in?

---

### Post by sikander3786 on 2012-04-17
Some times, I need to turn off my printer connected via USB cable to navigate through the Grub menu using my USB keyboard. Its weird but thats how it is.

If you haven't already, pull out all other USB cables including the mouse and see if your keybaord works then.

---

