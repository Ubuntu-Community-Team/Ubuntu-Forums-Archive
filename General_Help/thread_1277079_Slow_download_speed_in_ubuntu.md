---
title: "Slow download speed in ubuntu"
date: 2009-09-27
forum: General Help
---

### Post by kumarprabhatn on 2009-09-27
Hi there.. I m using ubuntu 9.04. I get very slow download speeds. Check out the snapshots for example.
When I downloaded Ubuntu 9.04 I get 140kBps. I have tested it many times and in many sites and all of the times speeds wont exceed 150kBps. I tested the connection, here are the results.

[IMG]http://www.speedtest.net/result/576594114.png[/IMG]

I have set up connection in DSL and all IP and DNS are correct. In windows 7, I get full speeds  but here I m having some problem. Any solutions ?? Thanks in advance.

---

### Post by XCan on 2009-09-28
Is that screenshot from Windows or Ubuntu? It better be from Windows as the speeds surely are higher than 150 kB/s. You could always try and tune your tcp settings in sysctl.conf. I've had great success in high-latency servers doing it at least (increasing packet size mostly) [http://perfector.wordpress.com/2008/04/23/tweak-kernel-variables-in-sysctlconf/](http://perfector.wordpress.com/2008/04/23/tweak-kernel-variables-in-sysctlconf/) .

---

