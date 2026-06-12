---
title: "blackberry issues"
date: 2010-11-10
forum: General Help
---

### Post by louis.roux on 2010-11-10
I use to be able to plug my blackberry into my computer through the usb cable and an icon would pop up on my desktop and I could access my phone files, like music files, on the computer.  Now when I plug it in nothing happens

---

### Post by Hippytaff on 2010-11-10
Was that with windows? I've had troubles with ubuntu and phones. You should be able to access the phone as an external storage device though, if you have an sd card in the phone.

what does
```

lsusb

```
return when you have the phone plugged in (type it in a terminal - open a terminal with CTRL+ALT+T)

---

### Post by SeijiSensei on 2010-11-10
> **Hippytaff said:**
> I've had troubles with ubuntu and phones.

A lot of us have these problems.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329).  Mine still fails to work as a USB mass storage device after upgrades from 8.04 through 10.10. I try again with each new major kernel upgrade, but so far nothing works.  Windows recognized the phone in both XP and 7.

Might I suggest one or both of you post your problem in the Launchpad bug report as well?  Maybe we can stir up the developers.

---

### Post by Hippytaff on 2010-11-10
> **SeijiSensei said:**
> A lot of us have these problems.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329).  Mine still fails to work as a USB mass storage device after upgrades from 8.04 through 10.10. I try again with each new major kernel upgrade, but so far nothing works.  Windows recognized the phone in both XP and 7.

Always good to keep a windows partition or spare pc with windows on just incase you have to use it...all to do with non-open source barsta...I mean proprietary software :-)

---

