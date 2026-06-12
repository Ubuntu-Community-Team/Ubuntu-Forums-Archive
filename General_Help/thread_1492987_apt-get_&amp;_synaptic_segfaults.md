---
title: "apt-get &amp; synaptic segfaults"
date: 2010-05-25
forum: General Help
---

### Post by feistybill on 2010-05-25
Using Ubuntu 10.04... I'm seeing lots of these in my dmesg:

```

[  987.982676] synaptic[1729]: segfault at 0 ip 08321d40 sp bfedcb5c error 4 in libc-2.11.1.so[8241000+153000]
[ 1139.038407] synaptic[3480]: segfault at 0 ip 08321d40 sp bfedcb5c error 4 in libc-2.11.1.so[8241000+153000]
[ 1798.486322] synaptic[3761]: segfault at 0 ip 0393ed40 sp bff26bec error 4 in libc-2.11.1.so[385e000+153000]
[ 1849.631031] apt-get[5185]: segfault at 0 ip 00392d40 sp bfa2513c error 4 in libc-2.11.1.so[2b2000+153000]
[ 1900.094076] apt-get[5950]: segfault at 0 ip 002bbd40 sp bf928d4c error 4 in libc-2.11.1.so[1db000+153000]
[ 1964.590610] apt-get[6018]: segfault at 0 ip 00795d40 sp bf8b6c3c error 4 in libc-2.11.1.so[6b5000+153000]
[ 2166.178044] apt-get[7256]: segfault at 0 ip 00363d40 sp bfefc37c error 4 in libc-2.11.1.so[283000+153000]
[ 2429.974479] apt-get[7389]: segfault at 0 ip 001f0d40 sp bfb109ac error 4 in libc-2.11.1.so[110000+153000]
[ 2446.237873] apt-get[7427]: segfault at 0 ip 0030cd40 sp bffa230c error 4 in libc-2.11.1.so[22c000+153000]
[ 2651.264600] apt-get[7845]: segfault at 0 ip 008b9d40 sp bfa22e4c error 4 in libc-2.11.1.so[7d9000+153000]

```

However this only seems to happen when apt-get finishes installing a new package. Apart from the messages, everything seems to work fine... any ideas?

---

### Post by dino99 on 2010-05-25
install locate, then into console:

locate libc-2.11.1.so

and remove it, update upgrade

---

### Post by feistybill on 2010-05-25
Manually moving libc-2.11.1.so from /lib didn't help, and uninstalling libc is not possible (a huge list of packages depends on it)... Any other ideas?

---

### Post by dino99 on 2010-05-25
sudo aptitude update -q && sudo aptitude -q safe-upgrade

---

### Post by beumont2 on 2010-05-26
I have the same Problem, after installing on 10.04 the Mail Notification pkg and configuring it with my my google acount settings I am getting the following error every time a try to start the mail notification application:

May 26 18:01:40 workstation kernel: [ 3200.500560] mail-notificati[6687]: segfault at 373 ip 0413950b sp b7559aec error 4 in libc-2.11.1.so[40f9000+153000]
May 26 18:01:51 workstation kernel: [ 3211.605029] mail-notificati[6692]: segfault at 373 ip 07cca50b sp b7644aec error 4 in libc-2.11.1.so[7c8a000+153000

Any advice ?

---

### Post by fatsdt on 2010-06-07
I had apt-get consistently segfaulting on me because /var/log/apt did not exist.  

It stopped after I created /var/log/apt

---

### Post by whit on 2010-07-24
> **dino99 said:**
> sudo aptitude update -q && sudo aptitude -q safe-upgrade

This is not good advice. It just plain doesn't work. In fact, it breaks things even more to remove the library. Multiple segfaults on running aptitude -q safe-upgrade.

---

### Post by sqn on 2011-12-09
> **fatsdt said:**
> I had apt-get consistently segfaulting on me because /var/log/apt did not exist.  

It stopped after I created /var/log/apt

This is what worked for me. I have Leeenux V4,which is in fact 
cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

---

### Post by nothingspecial on 2011-12-09
And we bid you ***Goodnight, goodnight, goodnight*** .......

---

