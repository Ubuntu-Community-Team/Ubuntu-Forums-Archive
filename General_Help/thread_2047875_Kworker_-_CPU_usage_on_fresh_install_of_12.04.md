---
title: "Kworker - CPU usage on fresh install of 12.04"
date: 2012-08-25
forum: General Help
---

### Post by marchwarden on 2012-08-25
Hi guys,

Wondering if someone can point me in the right direction for a solution to this problem.  My fresh 12.04 install keeps locking up every ~30s.  The culprit, from what I can gather from top is a kworker process maxing out the cpu (this is a single core machine).  So far googling has  pointed me to a load of bug reports that make little or no sense to me other than indicating that the bug being reported was fixed, so I am at a loss as to how to fix my problem.

Any takers?

---

### Post by Bashing-om on 2012-08-25
marchwarden...

 I am not much knowledgeable help. But I did run across these:
a synopsis of the cause:
[http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu](http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu)
here is a fix that may or may not apply:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793)
same fix:
[http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/](http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/)
here is another fix:
[http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)
////
Maybe these will give you some indications of what to trouble shoot for.

[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by marchwarden on 2012-08-29
Thanks for the links, I ended up applying this fix in the end:

```
#echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf

```

---

### Post by dcstar on 2012-08-30
> **marchwarden said:**
> Thanks for the links, I ended up applying this fix in the end:


Then **Mark The Thread**.

---

