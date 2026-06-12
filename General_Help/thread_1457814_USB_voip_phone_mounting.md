---
title: "USB voip phone mounting"
date: 2010-04-19
forum: General Help
---

### Post by Tappet Head on 2010-04-19
Hello, new to Linux and decided after a few versions to go with Karmic, so far I have been lucky and got things sorted, but its all new to me so need help from the most basic.

I have Skype and decided to get a USB phone, skyfone, If I "lsusb"  I get its device details, but unsure of how to mount it or get it switching correctly. ID is 6993:b001

so any help with this new learning curve will be great

Cheers
TH :guitar:

---

### Post by P4man on 2010-04-20
You mean something like this:
[http://www.trademe.co.nz/Computers/Peripherals/Other/auction-280245434.htm](http://www.trademe.co.nz/Computers/Peripherals/Other/auction-280245434.htm)

If so, long story short, forget it. I spent ages trying to get my dect/skype phone working on linux, but it just doesnt work. Its recognized as a USB audio device, but there is no way to get it working with skype (from linux). I ended up running windows in a virtual machine on one of my ubuntu machines just to drive the skype phone and even that didnt work quite well as sound was choppy.

I would suggest either buying a wifi skype phone that works independent of your PC, or stick with a headset or desktop microphone.

---

### Post by Tappet Head on 2010-04-24
yeah, I have the same problem, I went to usbphoneworld.com and found skypemate for feodora, but cant get it to work with ubuntu. I tried the Vm but couldnt get the sound or usb to mount onto the virt machine to make it work.

Cheers 
TH:guitar:

---

### Post by Tappet Head on 2010-04-25
Ok, if I put this into terminal

 '/home/******/Downloads/install-SkypeMate'  I get install, yes no, then My terminal changes screen to a test thingo with a bar in the middle, it will move up and down depending on the buttons and so forth, but exits if you hit hang up, I have no idea on what to do with it from there. but I get a new icon on my screen for skypemate, but when I click it I get  " This link cannot be used, because its target "/usr/bin/SkypeMate" doesn't exist." so guessing I need to repair the link maybe?

---

### Post by Tappet Head on 2010-04-25
and when I exit I get this in terminal

alsactl: save_state:1530: Cannot open /var/lib/alsa/asound.state for writing: Permission denied
ln: creating symbolic link `/home/dennis/Desktop/SkypeMate': File exists

---

