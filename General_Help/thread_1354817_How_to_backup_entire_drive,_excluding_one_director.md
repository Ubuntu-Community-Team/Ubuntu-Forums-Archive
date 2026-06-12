---
title: "How to backup entire drive, excluding one directory?"
date: 2009-12-14
forum: General Help
---

### Post by sgiandubh on 2009-12-14
I have a network storage device with which I'm screwing around at the root level. I'd like to backup the entire drive, excluding one directory in which there is ~500GB of data, onto a USB drive connected to the device. Just in case the device gets dusted. I tried cp-R'ing one directory at a time, but some directories/files such as /dev output "operation not permitted." How do I backup the entire drive, excluding the /nethdd directory, without running into permission errors? Thank you.

---

### Post by audiomick on 2009-12-14
try looking at
```
man cp
```
and see if you can work out the options there.

As far as the permissions goes,
```
sudo su
```
might help there. This is, as I understand it, like going one step up from "sudo". Be careful with it. It makes you a super user until you close the terminal, and doesn't ask questions if you tell it to break your system...;)

---

### Post by sgiandubh on 2009-12-14
The device is installed with some linux distro, but there is no sudo in this distro. It's very barebones. Kernel is Linux 2.6.12.6-arm1. I'm logged in as root.  The device is an Iomega StorCenter with v20.20 firmware, if you wanted to know.

---

### Post by ajgreeny on 2009-12-14
Have a look at rsync, a cli utility that will copy all you wish and allows exclusions of the type you want.

---

