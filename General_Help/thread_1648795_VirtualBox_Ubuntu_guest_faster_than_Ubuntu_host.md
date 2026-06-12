---
title: "VirtualBox Ubuntu guest faster than Ubuntu host"
date: 2010-12-19
forum: General Help
---

### Post by na_ka_na on 2010-12-19
Hi all,

I've recently installed Ubuntu 10.10 64 bit (say host H). I also installed Ubuntu inside VirtualBox on H using the same image (say Guest G).

I'm working on a fairly large java project. I've installed the same version of jdk (sun-java-6) on both H & G.

To compile my project - it takes ~3 mins 10 secs (consistently) on H, whereas it only takes ~1 min 5 seconds on G .  The full build (compile + tests) takes ~29 mins on H, whereas it takes only ~7 mins on G. Tests do a lot of writes to mongodb.

This is very puzzling. I think it has something to do with fsync disk io etc. But I'm not proficient enough to dig further. Maybe it has something to do with partition sizes of H, G?

Please help me understand this behavior.

Thanks!

---

### Post by na_ka_na on 2010-12-19
Ok I ran a few more tests and I guess that the culprit is indeed fsync. Is there a mechanism to tell Ubuntu to fysnc less often?

---

### Post by na_ka_na on 2010-12-27
Hello guys, any suggestions / insights regarding this?

---

### Post by karthick87 on 2010-12-27
Me too feel the same..VirtualBox Ubuntu guest is faster than Ubuntu host,i feel this when i try to browse a web page..When i try to browse a web page in ubuntu host  i feel it is little slower than the ubuntu guest..

---

### Post by noah++ on 2010-12-27
Reminds me of [this article I just read]("http://www.phoronix.com/scan.php?page=article&item=linux_kvm_virtualbox4"), a KVM vs. Virtualbox benchmarking analysis. Noticing that Virtualbox's performance exceeds its host's on some tests, it criticizes Virtualbox for not obeying fsync requests -- says it risks database integrity problems. Not that I'd be one to know if that's true.

---

