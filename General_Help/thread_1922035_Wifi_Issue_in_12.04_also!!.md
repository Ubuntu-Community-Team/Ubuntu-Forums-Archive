---
title: "Wifi Issue in 12.04 also??!!"
date: 2012-02-07
forum: General Help
---

### Post by ernestj on 2012-02-07
I have had a wifi issue ever since I upgraded from 11.04 to 11.10. It seems to be a kernel issue and a known bug for Asus U56. I had to backdate to Kernel 2.6 to get my wifi back. I download 12.04 and ran a live session. Still no wifi!!! Is this even being looked at or am I screwed and stuck in the dark ages with the old kernel.

Is there a way to compile a fix and customize the kernel?
Thanks, 
Ernie

---

### Post by dFlyer on 2012-02-07
If you've upgraded to Alpha 2 12.04 and have no wifi, have you filed a bug report. Doing so will hopefully have the problem fixed by the time 12.04 LTS is released.

---

### Post by uRock on 2012-02-07
Does the driver show up in Additional Drivers? What chip set does your wireless use? 

Are yous still trying to work this on 12.04 or are you using a supported release?

---

### Post by ernestj on 2012-02-08
See below for the last thread when I originally tired to fix the issue.

[http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie](http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie)

It explains my problem.

Where do I file a bug report. Even though it is a problem with the kernel.

Ernie

---

### Post by kaldor on 2012-02-08
> **ernestj said:**
> See below for the last thread when I originally tired to fix the issue.

[http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie](http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie)

It explains my problem.

Where do I file a bug report. Even though it is a problem with the kernel.

Ernie

Create a launchpad account. If you're on 12.04 run the command "ubuntu-bug" in the terminal and follow the steps. It will collect hardware data about your machine and then you can comment on the report.

You will need a wired connection.

---

### Post by ernestj on 2012-02-08
Thank you. I do have a wifi connection via 2.6 kernel. I access it when I log in.

---

### Post by uRock on 2012-02-08
> **ernestj said:**
> See below for the last thread when I originally tired to fix the issue.

[http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie](http://ubuntuforums.org/showthread.php?t=1889651&highlight=ernie)

It explains my problem.

Where do I file a bug report. Even though it is a problem with the kernel.

Ernie

This user seems to have gotten that same chipset working. [http://ubuntuforums.org/showthread.php?t=1795357](http://ubuntuforums.org/showthread.php?t=1795357)

---

### Post by ernestj on 2012-02-08
Thanks for the response. My wifi worked perfectly in 11.04. After 11.10 has not worked since. I have an ASUS U56, I will file a bug report, but I did this once like 6 months ago.

ernie

---

### Post by ernestj on 2012-02-10
Went to Lauchpad. A guy named Dave handled it and now it is working!!!!
Solved

---

### Post by ernestj on 2012-02-10
solved in Launchpad.

---

### Post by uRock on 2012-02-10
Can you please link the launchpad page here in case others need your fix?

Thanks

---

### Post by ernestj on 2012-02-11
This bug affects:

Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)

Link:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/187367](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/187367)

---

