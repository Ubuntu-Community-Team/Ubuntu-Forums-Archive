---
title: "ubuntu 11.04 slow performance"
date: 2011-05-11
forum: General Help
---

### Post by flipybcn on 2011-05-11
I've updated my main desktop to Natty, and the performance is getting worse and worse every day.

Changing between desktops it's slower and buggy, sometimes the left panel wouldn't go away or wouldn't appear, screensaver takes a long time to respond after it has been activated, and even graphic performance has decrease.

Is there anything I can do to improve the performance?

Computer is:
HP Compaq 6000 Pro SFF PC
Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz
4Gb ram
Intel Q45/Q43 Chipset
Intel Corporation 82801JD/DO (ICH10 Family)

I can provide as much information as needed.

Thanks

---

### Post by r-senior on 2011-05-11
As a start, could you have a look in /var/log/syslog, /var/log/dmesg and ~/.xsession-errors and see if there are any error messages that stand out? Anything that's really repetitive.

---

### Post by flipybcn on 2011-05-11
From the syslog I can't find anything relevant.

From the xsession-errors, there are a lot of them, but this one repeats almost always:
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags

However, seems to be related to accessing a SMB share partition (I guess).

From the dmesg log, I just can see this:
[   25.170334] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   25.170338] [drm] MTRR allocation failed.  Graphics performance may suffer.


And I don't know if it's wrong or not.

I could post the entire logs, but there are pretty big.

UPDATE: I've found out something related to the graphics performance: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677)

---

### Post by r-senior on 2011-05-11
> **flipybcn said:**
> From the dmesg log, I just can see this:
[   25.170334] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   25.170338] [drm] MTRR allocation failed.  Graphics performance may suffer.


And I don't know if it's wrong or not.
The words "failed" and "suffer" certainly suggest something's wrong. Whether that is what is causing your deterioration in performance is another question.

Looks like this bug, and there's a workaround at the bottom for you to try ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677)

Remember to run sudo update-grub (and reboot) after you modify /etc/default/grub.

---

