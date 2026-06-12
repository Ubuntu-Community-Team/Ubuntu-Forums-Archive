---
title: "Wireless broken after Karmic upgrade"
date: 2009-11-03
forum: General Help
---

### Post by Bit101 on 2009-11-03
After the Karmic upgrade and various problems I worked out by myself, I still cannot get my wireless to work in Karmic. The Network Manager applet has "Enable Wireless" greyed out and only works on ethernet. Interestingly enough, when I flip the wireless switch on my computer off (and I'm SURE I'm flipping it off then. No, I'm not just forgetting to turn wireless on), Wireless ungreys and begins trying to connect to my default network (which it fails since the wireless is off).
I had this problem back in Jaunty after a HAL update, which I fixed by downgrading HAL, but I can't do that in Karmic since the current HAL version is the only one available and I'm afraid I'll break numerous things if I downgrade just HAL.

Laptop is a Dell Vostro 1520, with a Broadcom BCM431 running Karmic.

Any help would be appreciated, but I understand if there's no posts after a while since there's so many help requests.

---

### Post by fooman on 2009-11-03
do you have the "bcmwl-kernel-source" package installed?

connect to the internet via ethernet....then search for it using synaptic  (system > administration > synaptic package manager)....if its not installed,  install it.  if it is installed,  reinstall it.

then reboot.

see if that helps.

---

### Post by Bit101 on 2009-11-09
Sorry for not replying in a while. I've been too busy to work on my laptop.

bcmwl-kernel-source was installed and I reinstalled it. No dice after the reboot, still no wireless. As I said, I think the problem is HAL related or that it's not detecting the card properly. I've checked, and the driver is definitely running.

---

### Post by Bit101 on 2009-11-09
Bump
(I know I shouldn't bump this early, but this is one of the few periods of time when I can work on it)

---

### Post by Bit101 on 2009-11-11
Solved after BIOS Upgrade.

---

