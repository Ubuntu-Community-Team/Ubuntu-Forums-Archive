---
title: "Extremely Long Boot Time On Netbook"
date: 2011-10-19
forum: General Help
---

### Post by jdenham on 2011-10-19
I have installed Ubuntu 11.10 via a USB drive. Everything about the install seemed fine. Upon reboot and subsequent reboots, it takes three and a half minutes to get a logon prompt. 

I have searched around and even tried disabling the legacy USB support as suggested by someone else but it only sped it up about 10 seconds. This particular netbook did have Windows 7 Starter ](*,) but has been ripped out and replaced with Ubuntu 11.10.

The netbook I am using is an NB305.

I check dmesg and it shows:
[    3.227316] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  209.045596] udevd[302]: starting version 173

This appears to be a big chunk of time missing. Not sure if it's relevant.

---

### Post by jdenham on 2011-10-19
So I installed bootchart to see if it would give me any clues as to whats going on. Now Ubuntu boots to a logon in 47 seconds :-k.

I uninstalled bootchart and now it's back to taking 3.5 minutes.

So, I will keep troubleshooting. If anyone has a clue as to whats going on here, feel free to chime in.

---

