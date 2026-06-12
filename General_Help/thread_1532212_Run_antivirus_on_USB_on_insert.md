---
title: "Run antivirus on USB on insert"
date: 2010-07-16
forum: General Help
---

### Post by ZD210 on 2010-07-16
Hi guys,

looking for some help with something I'm trying to get working.

I want to have a machine so that every time a USB drive is inserted into the system an antivirus is run to check it over.

I have started looking into solutions and have looked into the possibility of using Udev, the problem I've come across however is that you seem to have to specify the drive via either UID or name within Udev. However I believe Udev is the way forward.

The problem I face is that the system will not only have quite a high turnover of different USB drives, but also a high likelihood of having multiple drives plugged in at the same time.

The reason I mention this was because I was also looking into using the logs in /var/log/messages or dmesg to log the last inserted drive and use some python script to perform a task on the variable specified.

However I came across the problem of how to specify the variable using the logs using python script.

Any help would be appreciated.

Cheers.

---

