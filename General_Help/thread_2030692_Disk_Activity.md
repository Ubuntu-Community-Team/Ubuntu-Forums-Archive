---
title: "Disk Activity"
date: 2012-07-20
forum: General Help
---

### Post by doublez2 on 2012-07-20
I run Ubuntu Server Edition on my home server. I've noticed lately that my disk activity light has been blinking when nothings going on. The server is just a DHCP and DNS server. Ive noticed that the blinking is consistent. It seems like every three seconds the light comes on and stays on for a second. I assumed it was a cronjob set to run, but I couldnt find it, so is there a way to check which program is using your disk?

---

### Post by mardybear on 2012-07-21
Have you tried using your favourite system monitor utility. Example, run gnome-system-monitor in terminal, under the 'processes' tab look for the active status application or check active cpu usage.

Not sure if this is the case with your system but you can also use gnome-system-monitor to check swap file usage (resources tab). I used to have a fair amounnt of hard drive thrashing, adjusted by swappiness to reduced swap file usage and my system now runs nice and quiet.

Hope this helps,

mardybear

---

### Post by codemaniac on 2012-07-21
> **doublez2 said:**
> I run Ubuntu Server Edition on my home server. I've noticed lately that my disk activity light has been blinking when nothings going on. The server is just a DHCP and DNS server. Ive noticed that the blinking is consistent. It seems like every three seconds the light comes on and stays on for a second. I assumed it was a cronjob set to run, but I couldnt find it, so is there a way to check which program is using your disk?

There are some disk activity monitoring utilities you might be interested in .
Like ***iotop ***which shows you exactly disk-read and disk-write in bytes per seconds, per process. You can install it with ```
sudo apt-get install iotop
``` in Ubuntu.

---

