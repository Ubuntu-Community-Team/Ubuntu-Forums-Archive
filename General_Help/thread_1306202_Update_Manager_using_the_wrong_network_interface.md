---
title: "Update Manager using the wrong network interface"
date: 2009-10-30
forum: General Help
---

### Post by SteveDee on 2009-10-30
I have 2 machines linked together via ethernet cable, in addition to individual WiFi modules which provide internet access. I used gnome-network-admin to get the ethernet link to work as described here: [https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)

I've been using this setup for about 6 weeks and thought it was OK, until I noticed that one system has not received any updates for 45 days.

One system works perfectly in so far as I can use Firefox, Synaptic and Update Manager as expected. On the second system Firefox & Synaptic work OK, but the Update Manager tries to use the ethernet interface to retrieve data from the internet and fails with the comment "Unable to connect to 200.1.1.1 8080"

I could not see any differences between to two systems. And could not find a config setting for Update Manager to direct it to the WiFi interface.

I've now disconnect the ethernet cable and cleared the ethernet settings, but the problem persists.

Any ideas?

---

### Post by SteveDee on 2009-11-07
I'm still trying to workout where the network connections are defined for Update Manager...any ideas?

---

### Post by SteveDee on 2009-11-07
OK found the answer. Used grep in /etc and found the file "environment" referenced the bad IP as a proxy.

In terminal used "env" to confirm that proxy was set.

Went to System > Preferences > Network Proxy and found it had been set in here. Cleared it, used "Apply system wide" rebooted, job done!

---

