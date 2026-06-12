---
title: "Slow performance of Mozilla Firefox in Ubuntu 10.10"
date: 2010-11-20
forum: General Help
---

### Post by iokara08 on 2010-11-20
Good evening:),

I would like to report an issue regarding Mozilla Firefox in ubuntu 10.10.
Continuously, a slow performance is experienced whenever I am trying to browse through the web. It takes about 20 sec to load a page..... 
This issue was always existed in my system even when I was using the previous version of Ubuntu, 10.04.
Is there any solution about it?

Thank you all in advance!

Laptop:
Acer Aspire 5050
2GB DDR2 & AMD Turion 64

---

### Post by sohlinux on 2010-11-20
> **iokara08 said:**
> Good evening:),

I would like to report an issue regarding Mozilla Firefox in ubuntu 10.10.
Continuously, a slow performance is experienced whenever I am trying to browse through the web. It takes about 20 sec to load a page..... 
This issue was always existed in my system even when I was using the previous version of Ubuntu, 10.04.
Is there any solution about it?

Thank you all in advance!

Laptop:
Acer Aspire 5050
2GB DDR2 & AMD Turion 64

have you tried with other browsers in ubuntu like konqueror or  chromeum. are they also slow?

---

### Post by iokara08 on 2010-11-20
Hi again,

Yes I am using several browsers, Chrome, Epiphany and Chronium and no problems occur. I apologize for not mentioning it before.
Just the issue appears only when I make use of Mozilla Firefox.

---

### Post by ajgreeny on 2010-11-20
Have you disabled ipv6 in FF?.
If not type **about:config** in the addressbar and ignore the demons or dragons warning, but be careful.

Type ipv6 in the filter to search and in the line that appears
```
network.dns.disableIPv6;                user set              boolean               true
```
make sure it says **true** at the end.  If it is false, double click to toggle it to true and the leave the page.  You may need to restart FF, I can't remember if it's necessary.

---

### Post by iokara08 on 2010-11-21
Good morning all,

Hi ajgreeny,

Thank you for your useful information.
I just followed your instructions and now Mozilla exhibit a very good and balanced :-({|= performance!

Thank you all!
This thread will be marked as SOLVED:popcorn:

---

### Post by ajgreeny on 2010-11-21
Great!

Whether or not it matters seems to depend on your ISP's setup and how they send their broadband packets.  Very few ISPs or sites are using ipv6 yet as far as I understand things.

Anyway, I'm glad all is now sorted.

---

### Post by DocNaq on 2011-01-16
I had the same issue. This fixed my problem too.  Thanks!!

---

### Post by sephiclo on 2011-02-23
> **ajgreeny said:**
> Have you disabled ipv6 in FF?.
If not type **about:config** in the addressbar and ignore the demons or dragons warning, but be careful.

Type ipv6 in the filter to search and in the line that appears
```
network.dns.disableIPv6;                user set              boolean               true
```make sure it says **true** at the end.  If it is false, double click to toggle it to true and the leave the page.  You may need to restart FF, I can't remember if it's necessary.


Thank you very much, this was helpful. Just when I was about to dismiss my favorite browser :)

---

### Post by Winterdream on 2011-03-25
Thank you!  This problem showed up after installing updates and this solution worked perfectly! :)

---

