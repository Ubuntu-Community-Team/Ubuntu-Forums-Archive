---
title: "looking for something to send email when disk full, swapping, CPU pegged long time"
date: 2009-08-07
forum: General Help
---

### Post by meonkeys on 2009-08-07
Anyone know a simple utility that will send an email when the disk fills up, the system is doing a lot of swapping, or the CPU is pegged for a long time? logwatch seems likely, just looks like it does too much other stuff. Also, I don't want periodic emails "no matter what", only when certain conditions are met. I can't find any examples for "swatch", but it doesn't really look like what I want, either.

The sysstat utility (particularly "sar") seems to have exactly the information I need, I just didn't see an easy way to configure it to send condition-driven alerts.

---

### Post by dcstar on 2009-08-07
> **meonkeys said:**
> Anyone know a simple utility that will send an email when the disk fills up, the system is doing a lot of swapping, or the CPU is pegged for a long time? logwatch seems likely, just looks like it does too much other stuff. Also, I don't want periodic emails "no matter what", only when certain conditions are met. I can't find any examples for "swatch", but it doesn't really look like what I want, either.

The sysstat utility (particularly "sar") seems to have exactly the information I need, I just didn't see an easy way to configure it to send condition-driven alerts.

logcheck

---

### Post by blueridgedog on 2009-08-07
I used Big Brother for this back in the day:
[http://www.bb4.org/home1.html](http://www.bb4.org/home1.html)

---

### Post by meonkeys on 2009-08-08
> **dcstar said:**
> logcheck

Hmm, can you say more about how logcheck can be used to report disk full/swapping or CPU pegged for a long time conditions? It has even less documentation than swatch.

I actually use OpenNMS right now, and [it appears it is possible configure it to monitor disk space using SNMP]("http://www.opennms.org/index.php/Monitoring_disk_space_with_Net-SNMP") (although it hardly looks trivial).

---

### Post by meonkeys on 2009-08-08
> **blueridgedog said:**
> I used Big Brother for this back in the day

I prefer something that's already in the Ubuntu repositories. Is Big Brother proprietary?

---

### Post by blueridgedog on 2009-08-08
> **meonkeys said:**
> I prefer something that's already in the Ubuntu repositories. Is Big Brother proprietary?

It wasn't when I used it last.

---

### Post by meonkeys on 2009-09-22
> **meonkeys said:**
> Anyone know a simple utility that will send an email when the disk fills up, the system is doing a lot of swapping, or the CPU is pegged for a long time?

We ended up setting up OpenNMS monitoring using SNMP. Works well! It sends emails when a system is thrashing, disks fill up, or system load is too high. In case anyone is interested, here are details on how we set it up:

[http://www.mifos.org/developers/wiki/MonitoringSeversWithOpenNMS](http://www.mifos.org/developers/wiki/MonitoringSeversWithOpenNMS)

Custom "thresholds" can be used monitor and send notifications. SNMP can be used to report on pretty much any aspect of a running operating system. SNMP is easy to setup, but OpenNMS took quite a bit of fiddling to get right.

---

