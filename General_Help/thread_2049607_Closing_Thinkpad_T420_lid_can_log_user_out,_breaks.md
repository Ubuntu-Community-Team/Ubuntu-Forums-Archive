---
title: "Closing Thinkpad T420 lid can log user out, breaks network manager etc."
date: 2012-08-28
forum: General Help
---

### Post by brandizzi on 2012-08-28
Hello, all.

I am using a ThinkPad T420 running precise and when I close the lid sometimes I am logged out and all of my applications are forcefully closed. A lot of bad things follow:

* It takes an awful lot of time to log in again.
* When I log in, the look-and-feel of the desktop is considerably changed, using different fonts than the default ones used by Unity.
* The network manager is down and I should restart it with "/etc/init.d/network-manager restart".
* Control+Alt+BackSpace does not restart X
* I cannot acccess any text terminal. When I press Control+Alt+F1/F2.../F6, no login prompt is presented. Instead, I just see something like this:

[drm] nouveau 0000:01:00.0: POSTing device...
[drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x73B5
watchdog: only one watchdog can use /dev/watchdog.
watchdog: error registering /dev/watchdog (err=-16).
mei: unable to register watchdog device.
sd 0:0:0:0: [sda] Starting disk
[drm] nouveau 0000:01:00.0: 0x7393: i2c wr fail: -6
[drm] nouveau 0000:01:00.0: 0x73A5: i2c rd fail: -6

(I use to see this log everytime I reopen the lid, even when the problem does not happen).

Does anyone have this problem, too? It is becoming really annoying, because I am losing a lot of time rebooting my machine and .sometimes I lost some work I did. Worse, sometimes I put the notebook in my backpack and, since it is not sleeping, it heats as hell. I am afraid it can damage even my hardware :(

(Also, the apport suggested me to open a bug report and [I just did it]("https://bugs.launchpad.net/ubuntu/+bug/1030387"). If someone has some ideas, it has a lot of info)

---

