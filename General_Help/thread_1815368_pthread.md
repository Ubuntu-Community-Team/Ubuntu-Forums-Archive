---
title: "pthread"
date: 2011-07-31
forum: General Help
---

### Post by mk631219 on 2011-07-31
Hi Everyone,
I have looked to see about how to download the program pthread so that I can use
[**avast! Linux Edition (DEB package)**]("http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb")on it and can not find it. could you please let me know how I should download this into my ubuntu 10.4 operating system.
mk631219
PS. I tried all three of them and I get a bad message after it is finished or a list to try to download on the computer.

---

### Post by Gyokuro on 2011-07-31
The pthread library is already on your system, you can install avast4workstation via:

dpkg -i avast4workstation_1.3.0-2_i386.deb

or on a 64-Bit system:

dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb

HTH

---

