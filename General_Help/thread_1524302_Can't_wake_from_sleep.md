---
title: "Can't wake from sleep"
date: 2010-07-05
forum: General Help
---

### Post by Darkness Des on 2010-07-05
Whenever I close my laptop lid or just press the suspend button, it will go to sleep just fine. Perfect. Waking up is the problem. The drive light flashes for a few seconds, and then it just goes to back to normal but my display is still busted. Any suggestions?

---

### Post by clrg on 2010-07-05
Here's one: Reboot your computer and check /var/log/messages and /var/log/syslog

Also, do you get a terminal when pressing Ctrl + Alt + F1-6?

Did you install a proprietary graphics driver?

---

### Post by Darkness Des on 2010-07-05
In short: I did but how do I post it, Nope, and none are needed/found.

---

### Post by brown12 on 2010-07-05
Des, I've had similar problems. Desktop (not laptop), U 10.04 amd64. Until a few weeks ago, suspend worked fine. Now resuming from suspend fails to resume the monitor and USB peripherals.

While I haven't managed to fix the suspend issue, I have found that removing NetworkManager.state is a good way to restore network functionality after a hard power down and reboot.

Potentially related: as of this week, shutdown fails and causes a reboot instead, leading to an endless cycle of reboots.

(Yes, I'm using the Nvidia driver, supposedly the current version.)

Good luck, please post a solution if you find it.

---

### Post by Darkness Des on 2010-07-05
Hmmm... I'm also using the amd64 version. My Intel graphics card (HD Media Accelerator) strangely needs no driver. I think our suspend problem may be the x86_64 version.

---

### Post by Meskarune on 2010-07-06
Do you have enough swap space to suspend your computer? You need a swap the save size as the amount of ram you have

---

### Post by clrg on 2010-07-06
That's not true. You need the amount of RAM * 1.2 of Swap space for hibernation (suspend to disk). For standby (suspend to RAM) you don't need additional disk space.

---

### Post by Darkness Des on 2010-07-06
My RAM is 4 gigs. My swap is 5 gigs. It can't be an issue with that.

---

### Post by Meskarune on 2010-07-07
What type of laptop do you have? Some laptops will only work with pm-utils and some will only work with kernel commands to return from sleep. (you can edit that in your keyboard settings)

---

### Post by Darkness Des on 2010-07-08
I have a Dell Inspiron 1564.

---

