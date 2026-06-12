---
title: "can't see left side of grub menu"
date: 2011-01-13
forum: General Help
---

### Post by Dutch70 on 2011-01-13
I noticed it after booting a Linux Mint-10- live usb, and had to do a **hard reboot**.

 My grub resolution has always been 640x480. after booting to the live usb & hard reboot(rseiub didn't work), the menu is shifted to the left and I can't see the left side of it anymore. About 1" of the words are not showing.

I've changed the resolution to 800x600 and I can see it now, but wonder why it happened and how to get it back the way it was. Not sure what else may have been affected.

Any help would be greatly appreciated.

Ps. I dual boot Vista & Maverick 10.10 but "about ubuntu" says I'm using 11.04 :confused: and I am not.

Any help would be greatly appreciated.

---

### Post by Quackers on 2011-01-13
The reboot letters are REISUB, or that works for me :-)
There is a known bug at the moment, which causes 10.10 to be shown as 11.04 in "about ubuntu". It affects nothing else. No need to worry.
As for your main problem, I'm afraid I don't have an answer. Why the resolution should suddenly change I have no idea :-(  A grub update, possibly?

---

### Post by Dutch70 on 2011-01-13
Yeah, REISUB seems to confuse people that use the skinny elephant thing. :D

At first I thought maybe running Linux Mint Live changed it, by   possibly changing the version of Syslinux to an older one, not sure if that would cause it, but then I remembered the hard reboot.

The resolution didn't change. I thought it had at first, until I started changing it around. Come to find out, the screen just shifted to the left an inch or two. 

 I had to change the resolution to 800x600 myself just to get all the words on the screen. It's not in my monitor settings either because it's the only thing that is shifted to the left.

---

### Post by KeyserSoze93 on 2011-01-14
> **Dutch70 said:**
> Yeah, REISUB seems to confuse people that use the skinny elephant thing. :D

At first I thought maybe running Linux Mint Live changed it, by   possibly changing the version of Syslinux to an older one, not sure if that would cause it, but then I remembered the hard reboot.

The resolution didn't change. I thought it had at first, until I started changing it around. Come to find out, the screen just shifted to the left an inch or two. 

 I had to change the resolution to 800x600 myself just to get all the words on the screen. It's not in my monitor settings either because it's the only thing that is shifted to the left.

That doesn't necessarily mean it's not the monitor settings. Monitors seem to store positional information for each resolution/refresh rate combination separately. For instance a screen can look find on 1024x768@60 but but off centre on 1024x768@85.

I'm not sure to what degree this applies to TFT, but I've noticed that when installing the NVidia restricted drivers I then had to reposition my picture, since they may the graphics card output about 1 cm to the left of what it had done before.

---

### Post by KeyserSoze93 on 2011-01-14
> **Dutch70 said:**
> Yeah, REISUB seems to confuse people that use the skinny elephant thing. :D

At first I thought maybe running Linux Mint Live changed it, by   possibly changing the version of Syslinux to an older one, not sure if that would cause it, but then I remembered the hard reboot.

The resolution didn't change. I thought it had at first, until I started changing it around. Come to find out, the screen just shifted to the left an inch or two. 

 I had to change the resolution to 800x600 myself just to get all the words on the screen. It's not in my monitor settings either because it's the only thing that is shifted to the left.

That doesn't necessarily mean it's not the monitor settings. Monitors seem to store positional information for each resolution/refresh rate combination separately. For instance a screen can look find on 1024x768@60 but but off centre on 1024x768@85.

I'm not sure to what degree this applies to TFT, but I've noticed that when installing the NVidia restricted drivers I then had to reposition my picture, since they may the graphics card output about 1 cm to the left of what it had done before.

---

### Post by KeyserSoze93 on 2011-01-14
> **Dutch70 said:**
> Yeah, REISUB seems to confuse people that use the skinny elephant thing. :D

At first I thought maybe running Linux Mint Live changed it, by   possibly changing the version of Syslinux to an older one, not sure if that would cause it, but then I remembered the hard reboot.

The resolution didn't change. I thought it had at first, until I started changing it around. Come to find out, the screen just shifted to the left an inch or two. 

 I had to change the resolution to 800x600 myself just to get all the words on the screen. It's not in my monitor settings either because it's the only thing that is shifted to the left.

That doesn't necessarily mean it's not the monitor settings. Monitors seem to store positional information for each resolution/refresh rate combination separately. For instance a screen can look find on 1024x768@60 but but off centre on 1024x768@85.

I'm not sure to what degree this applies to TFT, but I've noticed that when installing the NVidia restricted drivers I then had to reposition my picture, since they may the graphics card output about 1 cm to the left of what it had done before.

---

### Post by KeyserSoze93 on 2011-01-14
> **Dutch70 said:**
> Yeah, REISUB seems to confuse people that use the skinny elephant thing. :D

At first I thought maybe running Linux Mint Live changed it, by   possibly changing the version of Syslinux to an older one, not sure if that would cause it, but then I remembered the hard reboot.

The resolution didn't change. I thought it had at first, until I started changing it around. Come to find out, the screen just shifted to the left an inch or two. 

 I had to change the resolution to 800x600 myself just to get all the words on the screen. It's not in my monitor settings either because it's the only thing that is shifted to the left.

That doesn't necessarily mean it's not the monitor settings. Monitors seem to store positional information for each resolution/refresh rate combination separately. For instance a screen can look find on 1024x768@60 but but off centre on 1024x768@85.

I'm not sure to what degree this applies to TFT, but I've noticed that when installing the NVidia restricted drivers I then had to reposition my picture, since they may the graphics card output about 1 cm to the left of what it had done before.

---

### Post by Dutch70 on 2011-01-14
This monitor auto-adjusts and re-centers itself. There is no setting for it, that I'm aware of. Nothing else is off center, except for grub.


Edit:
Also found out the BIOS were offset as well, and after about 3 tries with monitor settings, that you were correct KeyserSoze93.
Thank you!!! 
Dave

---

