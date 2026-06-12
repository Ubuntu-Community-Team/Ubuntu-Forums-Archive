---
title: "SLLLOOOOOWWW Ethernet"
date: 2011-02-27
forum: General Help
---

### Post by Dans564 on 2011-02-27
Installed ubuntu on my friend's desktop and he "likes" it so far, except for the fact that he says his internet is super slow now.  He is on an ethernet connection so i don't see what could be going wrong. but does any1 have any suggestions i can pass his way?

---

### Post by Sef on 2011-02-27
1) System specs?

2) Cable, DSL, Other?

---

### Post by doas777 on 2011-02-27
well, the problem could be anywhere in the network stack, but in terms of ethernet itself, the best diagnostic tool is ethtool.

what is the output of: 
```

sudo ethtool eth0

```
replace eth0 with whatever interface name you are working with.

for web traffic, DNS queries can dramatically affect the perceived speed. 
here is the manpage for namebench, a dns benchmarker:
[http://manpages.ubuntu.com/manpages/maverick/man1/namebench.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/namebench.1.html)

and another article on dns benchmarking:
[http://odzangba.wordpress.com/2010/02/21/optimize-your-internet-speed-with-namebench-dns-benchmarking-tool/](http://odzangba.wordpress.com/2010/02/21/optimize-your-internet-speed-with-namebench-dns-benchmarking-tool/)

since the article is from last year, check to see if the packages mentioned are in the repos before downloading them from an external source or adding a PPA.

---

