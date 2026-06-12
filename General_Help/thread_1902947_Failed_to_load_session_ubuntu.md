---
title: "Failed to load session ubuntu"
date: 2012-01-01
forum: General Help
---

### Post by S.Clark on 2012-01-01
I recently switch from CentOS6 64bit to Ubuntu 11.10 64bit. Having a lot of trouble with the changes I struggle to install stuff but some how survived on past solved threads. Until later when I made the mistake of removing something I don't remember what exactly. Upon login via vnc I got "Failed to load session ubuntu". I assume I unistalled a KDE like package.

 I am totally confused as all I wanted to do was get srcds and teamspeak up and running.

I would reinstall if it wasn't for the fact my host charges me for OS reloads which is something I have never encountered while running under previous hosts for 3 years.

---

### Post by 2F4U on 2012-01-01
The file

/var/log/dpkg.log

should give you an overview what software has been installed or removed from the system.

---

### Post by elliotn on 2012-01-01
remove any NVIDIA related packages if u are not using a NVIDIA card, it worked for me b4, load rescue mode

---

### Post by S.Clark on 2012-01-02
> **2F4U said:**
> The file

/var/log/dpkg.log

should give you an overview what software has been installed or removed from the system.
Says permission denied.

Also my specs are

AMD Phenom II 840 3.2ghz x4
4GB DDR3 RAM
500 GB SATAII HDD

This is a server so quite important I'm able to get it working.

---

