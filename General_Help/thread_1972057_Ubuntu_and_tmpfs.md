---
title: "Ubuntu and tmpfs"
date: 2012-05-03
forum: General Help
---

### Post by dgharmon on 2012-05-03
Just upgraded to Ubuntu 12.04 Precise Pangolin and noticed I now have a tmpfs, is this normal? I don't have that much RAM and was wondering if it was cutting into this?
--

~ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        10G  6.7G  2.8G  71% /
udev            223M  4.0K  223M   1% /dev
tmpfs            93M  804K   93M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            233M   72K  233M   1% /run/shm

---

### Post by marinara on 2012-05-03
yeah it's eating 804K of your RAM

---

### Post by dgharmon on 2012-05-03
> **marinara said:**
> yeah it's eating 804K of your RAM

Or 93M ...

---

### Post by dcstar on 2012-05-03
> **dgharmon said:**
> Or 93M ...

That value seems to be fixed at 20% of available RAM:

[http://askubuntu.com/questions/122326/large-tmpfs-run-partition-must-it-be-so-big](http://askubuntu.com/questions/122326/large-tmpfs-run-partition-must-it-be-so-big)

---

### Post by dgharmon on 2012-05-07
> **dcstar said:**
> That value seems to be fixed at 20% of available RAM:

[http://askubuntu.com/questions/122326/large-tmpfs-run-partition-must-it-be-so-big](http://askubuntu.com/questions/122326/large-tmpfs-run-partition-must-it-be-so-big)

Well, I've gone back to version 11.04. That seems to have solved the issue. Never upgrade a working system.

---

### Post by dcstar on 2012-05-07
> **dgharmon said:**
> Well, I've gone back to version 11.04. That seems to have solved the issue. Never upgrade a working system.

There is no "issue", 12.04 and the kernel it uses simply do things **differently**.

---

