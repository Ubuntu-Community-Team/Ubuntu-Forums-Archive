---
title: "11: Resource temporarily unavailable"
date: 2012-09-27
forum: General Help
---

### Post by bacchus1903 on 2012-09-27
Hi 
I new to Linux ... when I try to remove libre office residual trace after a removal with Ubuntu installer,I got  a message like if some process is still running ...  I try to kill everything with *kill -9 -1* with no succes. and even the command *sudo apt-get update *do not work ???

Please give me some idea how to resolvemy problem 
Thanks in advance :lolflag::lolflag:


Here what happen when I try to remove Libre office
[I]anh@ubuntu:~$ sudo apt-get --purge remove libreoffice-core
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

And when I want to update apt-get:
[I]anh@ubuntu:~$ sudo apt-get update
[sudo] password for anh: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

---

### Post by cogier on 2012-09-27
Make sure nothing else that can install programs (e.g. Synaptic, Ubuntu Software Centre) is running and try again.

---

### Post by jerrrys on 2012-09-27
[More here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Resource+temporarily+unavailable+is+another+process+using+it&as_qdr=all&sa=Google+Search&lang=en")

---

