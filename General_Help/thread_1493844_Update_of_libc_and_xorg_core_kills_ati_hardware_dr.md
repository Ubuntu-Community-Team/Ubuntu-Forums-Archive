---
title: "Update of libc and xorg core kills ati hardware driver!!! HELP!"
date: 2010-05-26
forum: General Help
---

### Post by Bucky Ball on 2010-05-26
Hi friends,

As the title of the thread suggests, I got the weekly updates; libc files and an xorg core file from memory. Thinking now the xorg core possibly rewrote my xorg.conf!! This is one dumb update if so!

Anyhow, seems to have killed the restricted ATI driver. I can boot from kernel  2.6.24.26 but 27, the one I did the updates, after the Ubuntu progress bar I get a black screen. Booting from 26 I get the low resolution graphics guff and need to set it manually each time. Go to Sys->Admin->Hardware Drivers, and sure enough, the ATI driver is 'Not in Use'. Switch it on, try booting into 27, black screen.

Phew, back to 26, change to manual config, get back in, see ATI driver is off again, leave it off and leave manual graphics resolution and config, boot back into 27, everything is stretched and out of proportion!! But I can at least get in. Switch ATI driver on in there, reboot into 27, black screen ...

What is happening??? This is pretty urgent as my wife is end of semester uni stuff and needs this machine. Worse, so am I and have even more on the plate (but at least have a computer!), so ...

Any help appreciated. For the moment, any tips on how to reverse the changes would be great ...

Checked back through dmesg but can't find much. Any other ideas?

---

### Post by dino99 on 2010-05-26
try with x-swat ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

(select your release)

---

### Post by Bucky Ball on 2010-05-26
Thanks for that. Might have a look at that option over the weekend but don't want to screw up further. Don't have time to fix right now and this machine needs to be up, low graphics or not. 

Currently: in 27 kernel, fine with low graphics, ATI driver still there but disabled. If I switch it on, reboot, goes through progress bar fine then out of that to ... black screen.

More digging later but for now work to do!

---

### Post by karrank% on 2010-05-27
Can't offer any help other than to say the EXACT same thing has happened to me. Still trying to sort it out, thinking I need to uninstall ati drivers (unsure how) and reinstall the latest ati drivers(unsure how). Weird.

@ Dino: No option in dropdown menu for 8.04...ok to select 8.10 in this instance?

---

### Post by Bucky Ball on 2010-05-27
Yea, Dino. Just a reminder. Am using 8.04 LTS. :)

---

