---
title: "Reverted back to 9.04 from 9.10."
date: 2009-11-16
forum: General Help
---

### Post by old_geekster on 2009-11-16
I filed a bug report, but it didn't appear to help to date.  My problem was an Internet that took forever to open a page, link, etc.  I haven't seen anything that slow since I had a dial-up modem.  I was using Ubuntu way back then, as well.  By the way, this was with a clean install.

So, I decided to revert back to 9.04 to see if I was simply not remembering how it responded.  The difference is from 'click and wait' with 9.10 to 'click and jump' with 9.04.  The minute I click on a link it opens without delay.  There is definitely something going on with 9.10.

Has anyone else had any problems?  I am using DSL.

---

### Post by coffeecat on 2009-11-16
I've not had this issue - internet is as snappy as with Jaunty - but it seems some have. Have a look at this Launchpad thread:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Is this what you are experiencing? Have a look at post #7. It seems to explain it.

There are a number of workarounds mentioned there, and hopefully a fix will be forthcoming soon.

---

### Post by Giblet5 on 2009-11-16
9.10 w/ gigE ethernet to a DSL router here.

Static IP, in-house DNS server (also on 9.10).

My typical latency is 18ms with icmp roundtrip times in the 47ms range to a list of not-usually-busy internet servers.

Download speeds, as tested via [www.toast.net](www.toast.net) (shuttle+text) = 3788Kbps.

Everything is zippy. Same for three other desktops and two wifi-connected laptops.

Jaunty shows similar numbers, as does Win7.

Is it possible that you had a bad DNS server configured?

---

### Post by Mickser_52 on 2009-11-16
Hi, I had the same problem when I upgraded to 9.10. It seems to have something to do with IPV6 (whatever that is??).

I eventually found the following link  [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")      

 I tried the first suggestion 

In /etc/sysctl.conf one would add:

net.ipv6.conf.all.accept_ra = 0

and it worked for me. IPV6 was disabled and my email and browser recovered their normal speed.

---

### Post by old_geekster on 2009-11-16
Thanks for the replies.  I will give it another try later tonight.  I would like to use 9.10, although as I said, 9.04 is running great.

---

