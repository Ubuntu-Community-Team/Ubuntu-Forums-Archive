---
title: "linux-headers package not available for Dapper"
date: 2006-04-07
forum: General Help
---

### Post by s2h on 2006-04-07
I am trying to install vmware tools on Dapper Flight 5.  I have downloaded gcc but when I try to download the current linux-headers-2.6.15-19-386 I get a message that they are not available.  The only ones I have access to from the Package Manager are 2.6.15-20-386 eventhough I appear to be using 19.  Here is what I see:

user@ubuntu:~$ uname -r
2.6.15-19-386

user@ubuntu:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-19-386

Can anybody help?

Thanks

---

### Post by s2h on 2006-04-07
Never mind, I ran the smart update and when I rebooted the kernel changed to 2.6.15-20-386.

---

