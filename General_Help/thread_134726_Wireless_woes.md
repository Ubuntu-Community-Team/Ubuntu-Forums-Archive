---
title: "Wireless woes"
date: 2006-02-22
forum: General Help
---

### Post by aggiechemist on 2006-02-22
My wireless always starts up with encryption!!

I used to use my Kubuntu laptop at home, where I had an encrypted connection. I needed this feature. It worked, and life was great.

But now I can't turn it off. Right now, every time I reboot, I have to go to the command line and type

iwconfig eth0 enc off

which is painfully annoying. I just want that to happen automatically when the thing boots.

I have tried moving every setting in KDE related to wireless to have it automatically start in non-encrypted mode. I have even gone into the hidden config files in /home/USER/.kde/config and /root/.kde/config to try and delete the old keys out of the system. But it is still finding the keys somewhere and using them when the system boots.

Any suggestions?

---

### Post by Prospero2006 on 2006-02-22
My suggestion for a quick fix:

add that 'enc' line you have to type
to /etc/init.d/bootmisc.sh

Pros

---

### Post by aggiechemist on 2006-02-23
Thanks!!

I tried it. The sysem didn't like it though. It seems to suggest that the device eth0 hasn't been created yet, so it can't make any changes to it. I tried adding it to another script later in the boot process, but it seems to have the same issue. I'll try appending it to a few other scripts though, it seems like there  must be somewhere it will work.

---

