---
title: "error message entering Gnome session"
date: 2006-04-02
forum: General Help
---

### Post by harys on 2006-04-02
hi, i have this error message when i log in  my session in gnome : "could not look up internet address for harys. this will prevent Gnome for operating correctly. It may be possible to corret the problem by adding harys to the file /etc/hosts" then there are two options in tabs : "try to lock in  anyway" and "try again". need a help. thanks. harys

---

### Post by schilcha on 2006-04-02
Have a look at the file "/etc/hosts" -- as the error message suggests. The very first line of mine looks like this: 
```

127.0.0.1 smithers.springfield localhost smithers

```
Make sure, you've some entries in this file whith "harys" instead of "smithers" (which is my hostname) and your domain instead of "springfield", which is my local domain.

Good Luck!

---

### Post by harys on 2006-04-02
hi, i got into my /etc/hosts file and all information i could find there was : "# the following lines are desirable for IPV6 capable hosts. need another help! thanks. harys

---

### Post by Ramses de Norre on 2006-04-02
I've got this before the IPv6 lines: ```
127.0.0.1 localhost.localdomain localhost icarus
192.168.123.106 ramses

```
Where ramses is my username and icarus my host name (so terminal prompt is ramses@icarus). I'd try setting the first line as the first line of /etc/hosts (with your username of course).

---

### Post by harys on 2006-04-02
hi, when i saved the changes i have the answer that the permissions is denied. and when i tried to access root with sudo su i got this response : 
" sudo : unable to lookup harys via gethostbyname ( )"
  thanks so much. harys

---

### Post by taurus on 2006-04-02
You need to boot your system with the LiveCD.  Mount your partition where /etc is located and edit it that way...

---

