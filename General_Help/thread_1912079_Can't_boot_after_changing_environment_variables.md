---
title: "Can't boot after changing environment variables"
date: 2012-01-19
forum: General Help
---

### Post by nipunreddevil on 2012-01-19
I was trying to get FLip for AVR working.For that i needed to set environment variables for FLIP_HOME and for JAVA_HOME.I used export and also appended JAVA_HOME to /etc/environment.
After i restarted my system i am not able to boot.The boot process starts apache2 .But after that nothing happens.
I am using Lubuntu 11.10,dual booting with Win7

---

### Post by dcstar on 2012-01-20
> **nipunreddevil said:**
> I was trying to get FLip for AVR working.For that i needed to set environment variables for FLIP_HOME and for JAVA_HOME.I used export and also appended JAVA_HOME to **/etc/environment**.
After i restarted my system i am not able to boot.The boot process starts apache2 .But after that nothing happens.
I am using Lubuntu 11.10,dual booting with Win7

Boot off a Live CD/USB, mount the hard drive and edit that file.

---

### Post by nipunreddevil on 2012-01-20
> **dcstar said:**
> Boot off a Live CD/USB, mount the hard drive and edit that file.

Can't i use the root prompt from recovery console and do the same or would i have to use a live cd/usb

---

### Post by nipunreddevil on 2012-01-20
Went to recovery console and removed the entry JAVA_HOME from /etc/environment and the system is up and running again.I wonder why it happened in the first place

---

