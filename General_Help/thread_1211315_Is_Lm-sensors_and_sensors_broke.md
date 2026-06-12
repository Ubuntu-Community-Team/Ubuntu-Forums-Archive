---
title: "Is Lm-sensors and sensors broke?"
date: 2009-07-12
forum: General Help
---

### Post by VastOne on 2009-07-12
I have several systems running gkrellm and obviously lm_sensors

Over my last 4 builds using different Mobo's, I thought the failure of sensors was due to newer board sensors that lm_sensors was no up to date with.  

Due to a nVidia driver bombshell I had to reinstalled Ubuntu on a system where lm_sensors worked perfectly.  But following the exact install method I have always used, this system nw reports the same as the new 4, No Sensors Found

Anyone else seeing anything like this?

---

### Post by VastOne on 2009-07-12
Has anyone recently installed Ubuntu and gotten lm_sensors to work correctly?

---

### Post by Yellow Pasque on 2009-07-12
Try building lm-sensors from source. For Ubuntu 9.10/karmic: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418)

---

### Post by VastOne on 2009-07-12
> **Temüjin said:**
> Try building lm-sensors from source. For Ubuntu 9.10/karmic: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418)

This was the problem.  Thank you for the link and the insight. I do appreciate it.

For anyone else, I simply dloaded the deb from that launchpad site and installed it using gdebi and re-ran sudo sensor-detect. It identified the same info as the synaptic version but as it said at launchpad, this simply works.

---

### Post by NRDNick on 2009-09-12
Cheers, this fixed my issues with my mobo's(M2N32-SLI) sensors not showing up via lm_sensors. This is on Karmic btw.

---

