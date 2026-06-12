---
title: "Ubuntu Software Centre - connection cannot be Established"
date: 2011-01-10
forum: General Help
---

### Post by Ray Hamilton on 2011-01-10
Ever since I installed dansguardian (tinyproxy and firehol) I cannot access software using Ubuntu Software Center (nor with synpatic).  An example of the message I get: 

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgfortran3_4.4.3-4ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgfortran3_4.4.3-4ubuntu5_i386.deb) Could not connect to 127.0.0.1:8081 (127.0.0.1). - connect (111: Connection refused)

I have uninstalled dansguardian, tinyproxy and firehol (and clamav?) and re-booted. It still does not work.  I can access the internet as normal via Firefox and Chrome (obviously after I have "re-set" the proxy).

What do I need to do to be able to use USC again?

Thanks in advance for your help.

---

### Post by DogMatix on 2011-01-10
Try in USC navigating

Edit > Software sources

then select a different 'Download from' server

---

### Post by Ray Hamilton on 2011-01-11
Thanks, but "Edit > software sources" doesn't allow me to change the port and I think this is where the problem lies.

---

