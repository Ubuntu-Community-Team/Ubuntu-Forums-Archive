---
title: "Ubuntu 11.04 Crashes"
date: 2011-09-24
forum: General Help
---

### Post by kmansfield on 2011-09-24
I have a Lenovo X120e laptop that crashes suddenly.  I have looked through the logs and cannot see anything captured to help.  It is as though it has stopped so quickly that nothing got captured.  

This could very well be because I do not know what to look for in the logs. At first i thought it might be an issue with the wireless driver but as I understand it the Realtek adapter I have is supported on my Kernal version.

I have attached the kernal log because that seemed like the most relevant.

**Hardware**
version: ThinkPad X120e
width: 32 bits
capabilities:
	SMBIOS version 2.6,
	DMI version 2.6,
	SMP specification v1.4,
	Symmetric Multi-Processing
configuration:
	boot: normal
	chassis: notebook
	cpus: 2
	family: ThinkPad X120e
	uuid: 01572D33-7B50-CB11-A0BB-CE2E62FD397F

---

### Post by dino99 on 2011-09-24
nothing into /var/crash/ ?

logs are into /var/log/ and some errors into .xsession-errors

can it be a hardware issue ?: fans running, ram issue, not enough free space on partition(s) (see system monitor)

---

### Post by kmansfield on 2011-09-24
The var/crash directory is empty.  

I don´t think it is a hardware problem because it does not crash when I boot Windows.

There were lots of errors Xorg log with the ATI/AMD fglrx graphics driver so I removed it.

---

