---
title: "Update manager input/output error"
date: 2009-11-01
forum: General Help
---

### Post by tamuz07 on 2009-11-01
Hi

I'm relatively new to linux so any help you could give would be amazing.

Whenever I try to check for updates I get this error message

jacob@system76-pc:~$ sudo apt-get check
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.


How would I go about fixing this?

---

### Post by michy99 on 2009-11-01
I'm not sure if this will work or not, but it's worth a try:```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```Then try the apt-get command again.

---

### Post by tamuz07 on 2009-11-01
Thanks for your help but I had no luck. I have a backup of my system from before I sent the computer in for repairs (it just came back) I might just restore the old settings and see if that works.

---

