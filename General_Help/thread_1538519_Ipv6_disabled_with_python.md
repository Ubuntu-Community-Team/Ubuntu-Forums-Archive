---
title: "Ipv6 disabled with python"
date: 2010-07-25
forum: General Help
---

### Post by rumca.js on 2010-07-25
Hi

Since karmic koala I have a problem with Ipv6 enabled by default. I will not argue about the sensibility of this decision.

I have disabled ipv6 on my system by adding necessary entry in grub configuration.

Now on my system there is no huge delay between internet requests.

However I am developing application in python (pygtk) and simple urllib2 code have very long answer response time.
I think that ipv6 setting may be the problem.

Should I tamper with any other setting in system - I have lucid lynx installed?
I modified now file sysctl.conf in etc dir. I added net.ipv6.conf.all.accept_ra = 0 as it is written in [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
The problem remains.

I have no further ideas how to solve this problem. 
Maybe I should not use urllib2 and use wget instead in my python code...

---

### Post by wojox on 2010-07-25
If you disabled it from Grub it shouldn't be your problem. Did you do it like this [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

Sounds like it may be your code.

---

### Post by rumca.js on 2010-07-25
Yes, I did exactly same thing. I double checked now if correct file was modified and yes, it have been done correctly.

Following code takes about 10seconds to complete. I suppose it should be faster :P
```
import urllib2
response = urllib2.urlopen('http://python.org/')
html = response.read()
print html

```

However now I found out that if I launch wget from commandline the same thing happens. resolving host google takes ages.
Is the tty somehow different?

Internet works ok on browsers, email clients, IM GUIs...

Ok. I think the best way is to delete all ipv6 support, recompile the kernel without that support, or similar.

---

