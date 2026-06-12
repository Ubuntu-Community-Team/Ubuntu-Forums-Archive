---
title: "Problem starting the system"
date: 2010-04-14
forum: General Help
---

### Post by i.arnav on 2010-04-14
I use UBUNTU 9.04. Today morning at about 0900 hrs i tried upgrading Pidgin from the Synaptic Package Manager. Some 133 packages were downloaded forcefully by me and it showed some broken packages also. Then i restarted the system as it was required but got hanged. Now it gets hanged everytime after a few seconds of booting showing the following msg:

[I][B]mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (319) terminated with status 127[/B][/I]

Please help, how do I solve this problem or recover back my data.

---

### Post by WinterRain on 2010-04-14
To recover your data, you could pop in a live cd and hook up an external drive and copy the stuff over.

---

### Post by i.arnav on 2010-04-14
> **WinterRain said:**
> To recover your data, you could pop in a live cd and hook up an external drive and copy the stuff over.

hey when i tried to recover data through the live cd, the files and folders werent copied to the external drive.
It said you dont have permission and error.

plz help.

---

### Post by wulle489 on 2010-05-11
Hey
I got the same problem. How do I get around the permission-thing when booting from a live-CD/USB ?

---

### Post by cabbrick1243 on 2010-05-11
I am well aware that this post is old but,
please start the file manager as root then with 
sudo nautilus

---

### Post by wulle489 on 2010-05-12
ok, im bit of a noob.
How do I start file manager as root - and what is file manager (Nautilus?)

I typed sudo nautilus in a terminal and it helped that way that Im now allowed to SEE all the data on my drive and home folder, but I still cannot COPY it.

---

