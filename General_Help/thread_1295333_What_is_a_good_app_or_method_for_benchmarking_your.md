---
title: "What is a good app or method for benchmarking your system?"
date: 2009-10-19
forum: General Help
---

### Post by dhughes on 2009-10-19
With the imminent release of a stable Ubuntu 9.10 I was wondering what the best way or what application(s) to benchmark a system are.

 I know it would depend a lot of how your system is set up but an overall average would be nice to have to compare a new and old distribution on the same hardware. Even comparing old distros on old hardware or new light distros on old hardware to see how well it works compared to different distributions.

Sourceforge has a list of apps for Linux benchmarking [http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

 Have any of you used any of these apps (hdparm would be the most common) or frequently benchmark your systems to check for slowing performance?

This looks good too: [http://tldp.org/HOWTO/Benchmarking-HOWTO.html](http://tldp.org/HOWTO/Benchmarking-HOWTO.html)

---

### Post by XCan on 2009-10-19
I haven't personally used it, but there is the Phoronix Test Suite [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/) which can run tons of benchmark apps.

---

### Post by P4man on 2009-10-19
there is only one benchmark that really matters, and thats the one sitting behind the keyboard.

---

### Post by _sAm_ on 2009-10-19
> **XCan said:**
> I haven't personally used it, but there is the Phoronix Test Suite [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/) which can run tons of benchmark apps.

Phoronix Test Suite is good, and they often post test of different setups so you can compare your results with others. You can read about it here; [http://www.phoronix.com/scan.php?page=news_item&px=NzA3Mg](http://www.phoronix.com/scan.php?page=news_item&px=NzA3Mg) I think this app has got its own GUI now(more easy to use).

---

### Post by dhughes on 2009-10-19
> **XCan said:**
> I haven't personally used it, but there is the Phoronix Test Suite [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/) which can run tons of benchmark apps.

 Very interesting, thanks for the info!

---

### Post by JoelOl75 on 2009-10-20
glxgears is a simple terminal opengl benchmark program... No frills but it helps when tuning X

---

### Post by P4man on 2009-10-20
> **JoelOl75 said:**
> glxgears is a simple terminal opengl benchmark program... No frills but it helps when tuning X

Its not a benchmark. In the past the only way to make it show fps was running > glxgears -iacknowledgethatthistoolisnotabenchmark

Its not a benchmark, its a testing tool. Whatever numbers it gives you with different hardware or drivers says nothing about actual OpenGL performance in apps. You can have entirely opposite results.

---

