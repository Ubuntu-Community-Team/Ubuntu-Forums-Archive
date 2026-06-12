---
title: "lshw very slow on Precise"
date: 2012-06-27
forum: General Help
---

### Post by lu333031 on 2012-06-27
Command "lshw" takes about 30s to list the hardware details (with or without sudo) on ubuntu 12.04  (3.2.0-25 kernel) on an Intel Atom CPU based system. No other OS is installed.

It used to take about 3 seconds with ubuntu 7.10 (the last time the command was run).

What has changed and can the response be made faster? Using the -class option to get selective data does not speed up the total response time for reading the HW information.

Thank you.

Lu

---

### Post by Cheesemill on 2012-06-27
30 seconds is about right.

The current version of lshw probes for a lot more hardware than the 5 year old version that you have used previously.

---

