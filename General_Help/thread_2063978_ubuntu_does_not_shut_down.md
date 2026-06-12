---
title: "ubuntu does not shut down"
date: 2012-09-28
forum: General Help
---

### Post by harun3d on 2012-09-28
When I want to shut down ubuntu, he comes on the login screen.  I cannot shut it down.

---

### Post by kc1di on 2012-09-28
> **harun3d said:**
> When I want to shut down ubuntu, he comes on the login screen.  I cannot shut it down.

It would be helpful if we knew what your hardware is and what version of Ubuntu you are using?

There have been many bugs of this sort in the past and it depends upon Hardware drivers and sometimes network connections.
So give us a little more to go on and we will see if we can help.

---

### Post by harun3d on 2012-09-28
It is a HP Pentium(R) Dual-Core CPU E6500 @ 2.93GHz × 2
32 bit 250GB hd
ubuntu 12.04

---

### Post by critin on 2012-09-28
> **harun3d said:**
> When I want to shut down ubuntu, he comes on the login screen.  I cannot shut it down.

Are you absolutely sure you're clicking the Shut Down text and not the Log Out?
Shut Down in the last option in the list.

---

### Post by harun3d on 2012-09-28
yes 
I have clicked I guess 40 times until now to shut down and ubuntu has logged out instead of shutting down 40 times.  So I am sure

---

### Post by critin on 2012-09-28
> **harun3d said:**
> yes 
I have clicked I guess 40 times until now to shut down and ubuntu has logged out instead of shutting down 40 times.  So I am sure

Okay, try Log Out--who knows?  It might shut down.

---

### Post by kc1di on 2012-09-29
Ok did a little research maybe this page could be of help to you.
[https://bugs.launchpad.net/ubuntu/+bug/995647]("https://bugs.launchpad.net/ubuntu/+bug/995647")

In any event in a terminal please type the following and see if the machine will shut done from that:

```
sudo shutdown -h now
```

If it does it means that the system is capable and something else is wrong.

---

### Post by harun3d on 2012-10-14
```
sudo shutdown -h now
```This shut down the pc. Thanks. And also normal shut down with the shut down icon on the upper bar right worked.  I will see if it also will work in the future

---

### Post by offgridguy on 2012-10-15
Just curious. Do you have more than 1 user account?

---

### Post by harun3d on 2012-10-21
no more than one user account

---

