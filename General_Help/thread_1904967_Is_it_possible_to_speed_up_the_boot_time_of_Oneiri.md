---
title: "Is it possible to speed up the boot time of Oneiric?"
date: 2012-01-05
forum: General Help
---

### Post by Henkdroid on 2012-01-05
Hi, my machine booted up into Natty in 35~s now with Oneiric it takes 75~s is there any way to speed it up. I have tried the "quiet splash profile" trick but I don't think it worked as I use BURG. Thanks for all your help.
EDIT: Those images haven't turned out too well here's a link :[Photos]("https://plus.google.com/photos/116897472948279469826/albums/5694290657382884465?authkey=CI_Hv8jo5f3cyAE")

---

### Post by imachavel on 2012-01-05
mostly I don't believe booting speed has anything to do with your OS, it should have something to do with 

1) processor speed
2) hard disk drive rpm, or even better mbps reading and writing speed. I believe having a solid state drive can help, also raid in some cases improves boot time.
3) linux software buffers may be slightly better then windows
4) if I explain any more, I'll be confusing you, sorry. I am pretty sure it is more of a hardware interface and compatible hdd and processor speed then anything else. Once everything is booted, then ram makes a difference but at boot I believe it doesn't at all.

---

### Post by rsvancara on 2012-01-05
1.  Disable services that you do not need, like database servers, apache etc....
2.  Use a SSD
3.  Disable DHCP, takes a few seconds to obtain a lease, hard code your IP Address

---

### Post by efflandt on 2012-01-05
What hardware and type of drive are you booting?  If you look at dmesg (or /var/log/syslog) do you see any period of long pause before next entry?  I have never used bootchart and posted images of that are always too tiny to read.

For me grub menu to login prompt for 64-bit 11.10 ranges from 8 seconds (SSD on desktop in sig) to about 35 seconds for Acer Iconia W500P tablet PC (2 core 1 GHz AMD C-50) booting from internal USB connected SDHC. Login to desktop is about 2 seconds to under 15 seconds respectively.

Of course booting iso on USB can take longer as it uncompresses itself and probes hardware.

---

