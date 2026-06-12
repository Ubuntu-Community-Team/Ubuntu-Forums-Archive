---
title: "Boot problem - I have fixed this in the past but now forget"
date: 2012-05-21
forum: General Help
---

### Post by DarrenO on 2012-05-21
I have had this issue in the past and have fixed it in the past... but do not recall what I did to fix it. Basically, I am fairly confident what the issue is...

Problem:
System hangs on boot, some times just before password is entered, sometimes afterwards. No keystroke or mouse movement recognized once it has hung.

Symptoms:
When I boot my computer there are a series of entries in my fstab that mount network drives to my system. If I remove these entries, the system boots normally and with no issues. The network drives I am mounting are in DNS-323 boxes that power down the hardrives after a period of time. If I use a second computer to access the drives and "get them spinning" before I boot my computer, my computer boots normally with my fstab entries in place.

My fixes (possibilities that I vaguely remember):
1. I need to modify the order that processes start up on my computer so that the drives are mounted later or so that the mount process is more patient.
OR 2. I need to get networking up and running before the computer tries to mount the drives.

Anybody know how to fix?

Thanks!

Long live UBUNTU.

---

### Post by wilee-nilee on 2012-05-21
Just out of curiosity have you run this to check if the fstab UUID entries are correct.

```
sudo blkid
```

---

### Post by DarrenO on 2012-05-21
I had not run that. All it shows me is the UUID codes for the three partitions on my local hardrive, not the UUID codes for the CIFS mounted drives.

The entries in my fstab are like this for example:
//192.168.2.50/Videos /home/danger/Videos cifs username=admin,password= 0 0

These entries have worked for years and they work fine if I boot the computer without them (comment them out) then re-enable them and do "sudo mount -a".

DarrenO

---

### Post by DarrenO on 2012-05-25
Anybody? This one is driving me nuts. Takes a few reboots to make it all the way in.

Thanks!

---

