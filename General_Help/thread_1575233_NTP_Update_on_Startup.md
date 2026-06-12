---
title: "NTP Update on Startup"
date: 2010-09-15
forum: General Help
---

### Post by dmarques on 2010-09-15
Hi,
I'm running a Ubuntu 10.04 server in a secured zone on my network that has no access to the outside world. In that same zone, there is an NTP server which I setup my Ubuntu server to access in order to sync its time on a daily basis. Everytime I reboot my Ubuntu server, the clock goes back 4 hours, I guess since it cannot access the default Ubuntu NTP server. Is there a way to disable this from the startup and if so where do I do it, or can I set it to sync on startup with my NTP server?
 
Thanks

---

### Post by gmargo on 2010-09-15
If your clock is changing across a reboot, it's probably due to the wrong value of the UTC flag in **/etc/default/rcS**.  Check that file and if it says UTC=yes then flip it to no, or vice versa.  Then reboot, and see if that helps.

To alter the ntp-time-source machine for the **ntpdate** program, edit the **/etc/default/ntpdate** file and alter the **NTPSERVERS** list.

However **ntpdate** is only run at network-interface-up-time.  I highly recommend that you install the **ntp** package and configure it to point at your internal NTP server, which will keep your time as accurate as possible, continously.

---

### Post by blueridgedog on 2010-09-15
Gmargo may have you working, but have you checked the time zone of the system?

```
sudo tzconfig
```

Have you checked the hardware clock (bios)

```
sudo hwclock
```

---

### Post by dmarques on 2010-09-16
> **gmargo said:**
> If your clock is changing across a reboot, it's probably due to the wrong value of the UTC flag in **/etc/default/rcS**. Check that file and if it says UTC=yes then flip it to no, or vice versa. Then reboot, and see if that helps.
 
To alter the ntp-time-source machine for the **ntpdate** program, edit the **/etc/default/ntpdate** file and alter the **NTPSERVERS** list.
 
However **ntpdate** is only run at network-interface-up-time. I highly recommend that you install the **ntp** package and configure it to point at your internal NTP server, which will keep your time as accurate as possible, continously.
 
Thanks alot gmargo. I did these two mods and now the server works like a charm. It always syncs with my internal NTP server now.

---

