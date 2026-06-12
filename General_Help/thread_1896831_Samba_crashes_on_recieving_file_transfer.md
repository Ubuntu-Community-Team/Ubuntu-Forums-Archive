---
title: "Samba crashes on recieving file transfer"
date: 2011-12-17
forum: General Help
---

### Post by Onthax on 2011-12-17
I'm having an issue with my mythbuntu box

whenever i try to copy files to it from my windows 7 box, it will freeze and become unresponsive, i can only fix it by turning it off at the power.

Anyone have any tips on where to look?  samba logs dont show me anything.

I know it's not an I/O issue on the mdadm array and myth is constantly writing and reading from it.

Network works fine when i'm reading from the mythbuntu box, only when writing

---

### Post by 2F4U on 2011-12-18
Did you already look into the system log files? I have Samba running on a machine with Ubuntu Server 10.04 and have absolutely no problem with file transfer from and to the machine, even on large amounts of data. The limitation here is more the network than the I/O on the machine.

---

### Post by dcstar on 2011-12-18
> **Onthax said:**
> I'm having an issue with my mythbuntu box

whenever i try to copy files to it from my windows 7 box, it will freeze and become unresponsive, i can only fix it by turning it off at the power.

Anyone have any tips on where to look?  samba logs dont show me anything.

I know it's not an I/O issue on the mdadm array and myth is constantly writing and reading from it.

Network works fine when i'm reading from the mythbuntu box, only when writing

You have not supplied any information on what version of Samba/Ubuntu you are using, and:

[http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

---

