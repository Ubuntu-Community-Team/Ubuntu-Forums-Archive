---
title: "Broadcom Issue"
date: 2011-08-22
forum: General Help
---

### Post by TheNessus on 2011-08-22
OK, I just cannot figure this out.

I did a clean install of 11.04 64 bit (and then of 32 bit, same issue there). While installing, on the live USB, the broadcom driver that is naturally on the live image, works. It does so even before downloading the broadcom driver, I guess using an open-source driver initially. 

Anyway, once intallation is done, I log in, and wireless does not work. I mean, it does work, but it doesn't seem to scan for networks. after I reboot several times the driver suddenly appears not to work at all (networking grayed out). The issue with it working and not working after several reboots happened to me before on 10.10 and 10.04, where another reboot fixed it. But here the issue is weird, as I said - it appears to work but does not scan for networks. 

I'm seriously considering ditching ubuntu altogether, I just can't get the thing to work!

---

### Post by seawolf167 on 2011-08-22
Did you install the available driver after installation? If you have the option, use the newer STA over the B43 drivers as they work better. See if it can scan for SSIDs after you install the driver. 

Do you have any power settings (that are enabled) which are disabling the wireless adapter to save power?

---

### Post by MARP1961 on 2011-08-22
> **seawolf167 said:**
> Did you install the available driver after installation? If you have the option, use the newer STA over the B43 drivers as they work better. See if it can scan for SSIDs after you install the driver. 

Do you have any power settings (that are enabled) which are disabling the wireless adapter to save power?

I have to say that the STA driver is **not working** for many users with Broadcom wireless in Natty. Indeed a number of these people (myself included) have only managed to get wireless working by using the B43 driver. Natty, Dell laptops and Broadcom drivers seem a bit of a mess to me.

---

### Post by gandaran on 2011-08-22
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

