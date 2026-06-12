---
title: "64 bit software"
date: 2009-11-20
forum: General Help
---

### Post by yeeeev on 2009-11-20
Hi,

Is there some easy way to find out on a 64 bit Karmic if the software installed from the repos is 64 bit or 32 bit software?

Thanks!

---

### Post by running_rabbit07 on 2009-11-20
> **yeeeev said:**
> Hi,

Is there some easy way to find out on a 64 bit Karmic if the software installed from the repos is 64 bit or 32 bit software?

Thanks!

Synaptic Package Manager loads everything to match the version you installed. If you installed Ubuntu 64bit, you will get 64bit software and 32 for 32.

---

### Post by running_rabbit07 on 2009-11-20
If you go to /etc/apt/sources.list whatever version it shows there is the same as the software for Synaptic's list. As you see in the top list of mine, it is for AMD64.

---

### Post by yeeeev on 2009-11-20
What about proprietary software that is only available in 64 bit as an Alpha release? (Flash plugin...;))
I installed the ubuntu-restricted-extra. How can I know which Flash version came along with it, and if it's 32 or 64 bit?

---

### Post by yeeeev on 2009-11-20
bump

---

### Post by running_rabbit07 on 2009-11-20
Please do not bump your thread after less than 24 hrs. Ubuntu-restricted-extras loads 32bit, but it works well.

---

### Post by yeeeev on 2009-11-20
Thanks for your reply.
Is there any generic way to know if a package is 32 bit rather then 64 bit?

---

### Post by blueridgedog on 2009-11-20
Use the "file" command.  I installed the 64 bit flash version so mine indicates it as:
```

:~$ file /usr/lib/mozilla/plugins/libflashplayer.so 
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

---

### Post by yeeeev on 2009-11-21
Thanks!

---

