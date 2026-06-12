---
title: "Ubuntu 10.10 crash, now freezes during startup"
date: 2011-01-03
forum: General Help
---

### Post by StevenSteavis on 2011-01-03
Hi,

yesterday I was running update manager in ubuntu and my system froze completely. I had no other option but to manually switch of the PC. Then after restarting the PC I got some error lines but I can't remember what they said. It didn't matter which linux version I chose from GRUB, nothing worked.

Today when starting up shortly after the Ubuntu 10.10 screen with the blinking dots below it I see a dos type screen with only a flashing cursor and nothing happens.

Is there any way I can fix this? Or repair the ubuntu installation without loosing all my data/settings etc?

I'm running now from the live CD. I can access the disk drive that has ubuntu installed on it. I have XP running on a separate disk and I can boot into XP from my motherboard's bios boot menu.

---

### Post by StevenSteavis on 2011-01-03
if I remove "quiet splash" from the command line the system seems to freeze after:

[ 3.700038} USB 3.2: new full speed USB device using uhci-hcd and address 2

I really hope someone can help... :confused:

---

### Post by spantch101 on 2011-01-05
ok .. seems the problem has been with the pm-utils in synaptic if you are having this issue check synaptic and see if you are running 1.4... if you are remove it and reinstall older version 1.3 here [http://packages.ubuntu.com/de/lucid/...utils/download](http://packages.ubuntu.com/de/lucid/...utils/download) fixed my problem... i just unplugged my laptop and its running perfectly... thanks to aspera for this info on launchpad hope this works for you...after install of 1.3 reboot just in case ...let me know how it works out for you.

---

### Post by spantch101 on 2011-01-05
> **StevenSteavis said:**
> Hi,

yesterday I was running update manager in ubuntu and my system froze completely. I had no other option but to manually switch of the PC. Then after restarting the PC I got some error lines but I can't remember what they said. It didn't matter which linux version I chose from GRUB, nothing worked.

Today when starting up shortly after the Ubuntu 10.10 screen with the blinking dots below it I see a dos type screen with only a flashing cursor and nothing happens.

Is there any way I can fix this? Or repair the ubuntu installation without loosing all my data/settings etc?

I'm running now from the live CD. I can access the disk drive that has ubuntu installed on it. I have XP running on a separate disk and I can boot into XP from my motherboard's bios boot menu.

make sure to try runing in recovery mode safe graphics mode , if you can follow my instructions ... desktop or laptop?

---

