---
title: "Ubuntu update error"
date: 2012-05-03
forum: General Help
---

### Post by keltischdeutscher on 2012-05-03
Just because I need to state it, I'm an absolute newbie with Ubuntu/terminals. I had messed up my partition and only had Ubuntu 12.04 running when I tried making a dual boot from CD because the dual boot option wasn't given. My Ubuntu was working fine (had some internet problem that fixed itself) and after using the update manager tonight, it mentioned that my graphics were running on low and wouldn't boot past the black screen where it asks for my user and pass. Looked over a lot of help forum topics and tried the suggested "startx", "sudo apt-get install ubuntu-desktop", "sudo gdm", and tried re-installing xorg but I have no idea what I'm doing. I have the iso on both a disc and usb and need to know how to do a clean install of 12.04 if booting isn't possible. Thanks for any help :/

Sony Vaio S
i7-2620
500GB HD (partitioned Ubuntu to have 70gb)
AMD 6630 HD
64bit
4gb ram

---

### Post by Peter09 on 2012-05-03
Depending on whats the problem, try doing this initially.
 
While booting hold the shift key down. This will get you to a menu where you can select recovery mode using the arrow keys to move down to the option.
 
Once that boots you should get a menu which will contain an option to re-setup you graphics, initially try that and see if you can recover your installation.

---

### Post by keltischdeutscher on 2012-05-03
For a while it was showing an os error message when I was trying it, but now it's bringing up the grub menu. Selecting anything from graphics option just brings me back to the previous menu

---

### Post by Peter09 on 2012-05-03
It will bring you back to the recovery menu once it resets your graphics, have you tried rebooting since you did the reset graphics thing?

---

### Post by keltischdeutscher on 2012-05-03
Yeah, there are the 4 options. The "run in low-graphics mode for just one session" brings me to a completely black screen. Reconfigure graphics brings me back to the recovery menu. Troubleshoot the error flashes text for 1/3 of a second then goes back to the recovery menu. And the console login option just goes to the console login.

Rebooting after the first 3 all bring me to the black screen

---

### Post by Peter09 on 2012-05-03
Looks like you have screwed it somehow. Have you any data on this system that you wish to save? 
 
If not just boot into the LiveCD and go through the install process again. (use the[COLOR=red] "use the complete disk option"[/COLOR] if possible, althought this will clear your HD of everything.

---

### Post by keltischdeutscher on 2012-05-03
I pretty much have all of the data I need on my tb external hd. I had searched for info on it, but haven't been able to bring up the livecd or usb options because I had screwed up my windows partition and don't have my windows disk at my apartment. Would the option be in the grub menu or...?

---

### Post by Peter09 on 2012-05-03
Puzzled here - the LIVECD should have the option to do an install to the disk - were you using Wubi or dual booting in some way?

---

### Post by keltischdeutscher on 2012-05-03
No, when I had downloaded the livecd, my intention was to do a dual boot for W7 and 12.04, but there was no option for a dual boot so I followed a tutorial for partitioning (since I had never partitioned before). It directed me to make a new table and I ended up losing my windows boot option, and it would boot directly into 12.04. Worked for days and after using the update manager, now I can only get to the console login (won't boot into ubuntu) or the grub menu

---

### Post by keltischdeutscher on 2012-05-28
Still haven't found a solution to this. Can't past the terminal (console login?) to get to my dekstop. Is there any way to completely reinstall 12.04 from the terminal? I don't care about any of the files on my HD, and I'm hesitant to bring my Vaio to Sony. I have the iso on a CD and on my usb, just can't find any way to use those online.

---

### Post by Peter09 on 2012-05-28
Just boot into the liveCD, and once you have it running the desktop will have an icon to install Ubuntu. Choose the 'use entire disk' option. That will wipe the existing data and installations and install Ubuntu. You will lose your windows install.

---

### Post by Shadius on 2012-05-28
First, would you like to get rid of your Windows installation and have Ubuntu take over the entire drive?

---

### Post by keltischdeutscher on 2012-05-28
That's the thing though, when I messed up the partition, I lost the windows boot and was left with only Ubuntu (which I didn't really care about at the time). The only thing I can access right now is the terminal and couldn't find any command to get to my desktop or access the livecd

But yes, at this point, I'd just like to have Ubuntu running again on my laptop and I'll set up windows later. I'm using my old DELL (horrible laptop) and android tablet, but neither are good replacements for my Vaio (considering I'm a PC gamer).

---

### Post by Shadius on 2012-05-28
> **keltischdeutscher said:**
> That's the thing though, when I messed up the partition, I lost the windows boot and was left with only Ubuntu (which I didn't really care about at the time). The only thing I can access right now is the terminal and couldn't find any command to get to my desktop or access the livecd

But yes, at this point, I'd just like to have Ubuntu running again on my laptop and I'll set up windows later. I'm using my old DELL (horrible laptop) and android tablet, but neither are good replacements for my Vaio (considering I'm a PC gamer).

Ah, I see. You should be able to access the Ubuntu LiveCD by just putting it in the CD-ROM drive. Have your BIOS set to boot from CD-ROM (ask if you need help doing this). However, it's recommended that you install Windows first, then Ubuntu.

---

### Post by keltischdeutscher on 2012-05-29
haha... Bios... that thing I've never had to access... well my Vaio is back from the land of $1,700 unusable laptops. Now I know the failsafe fix for a problem like this in the future. Thanks, Shadius ^_^

---

### Post by Shadius on 2012-05-29
> **keltischdeutscher said:**
> haha... Bios... that thing I've never had to access... well my Vaio is back from the land of $1,700 unusable laptops. Now I know the failsafe fix for a problem like this in the future. Thanks, Shadius ^_^

:lolflag: Glad to help. ):P You learn a lot by breaking things!

---

