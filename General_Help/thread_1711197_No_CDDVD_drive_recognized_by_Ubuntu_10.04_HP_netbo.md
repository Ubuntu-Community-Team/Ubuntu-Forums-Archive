---
title: "No CD/DVD drive recognized by Ubuntu 10.04 HP netbook"
date: 2011-03-21
forum: General Help
---

### Post by bigspoon on 2011-03-21
Hello,
I'm running ubuntu 10.04 on HP netbook.

When I run the "df -h" command it generates information but nothing about my CD/DVD drive:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             451G  422G  5.4G  99% /
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  1.0M  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G  4.0K  1.5G   1% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
none                  451G  422G  5.4G  99% /var/lib/ureadahead/debugfs
/home/ethan/.Private  451G  422G  5.4G  99% /home/ethan


What can I do to trouble shoot this?

Anyone?

---

### Post by troll1602 on 2011-03-21
So, the command "df" is used to report file system disk space usage, that means information about how the hard drive is organized, not the CD/DVD drive. When you call it with the "-h" it puts the numbers in a "human readable" format.

In short the "df" command shouldn't tell you anything about your CD/DVD drive.

Was there some other problem that lead you to believe that your CD/DVD drive was not being recognized?

---

### Post by Script Warlock on 2011-03-21
after installing libcdio-utils

cd-info
cdrecord &#8211;inq

---

