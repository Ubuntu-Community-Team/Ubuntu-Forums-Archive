---
title: "How to test network speed?"
date: 2006-05-08
forum: General Help
---

### Post by david049 on 2006-05-08
Hello,

I am setting up a wireless bridge between two wired networks, and I would like to find a way to measure network speed so I can examine the performance impact of various settings.

Is there software that I can use to plot graphs of various things like latency vs. throughput vs. concurrency, etc?

Thank you,
David

---

### Post by Sendervictorius on 2006-05-09
I suggest netpipe-tcp may be the answer. You can get in from synaptic

A network performance tool using the TCP protocol
NetPIPE is a protocol independent performance tool that encapsulates
the best of ttcp and netperf and visually represents the network
performance under a variety of conditions. By taking the end-to-end
application view of a network, NetPIPE clearly shows the overhead
associated with different protocol layers. NetPIPE answers such
questions as: how soon will a given data block of size k arrive at its
destination? Which network and protocol will transmit size k blocks
the fastest? What is a given network's effective maximum throughput
and saturation level?  Does there exist a block size k for which the
throughput is maximized? How much communication overhead is due to the
network communication protocol layer(s)? How quickly will a small (< 1
kbyte) control message arrive, and which network and protocol are best
for this purpose?

This package uses a raw TCP protocol to measure network performance.

---

### Post by david049 on 2006-05-09
[QUOTE=Sendervictorius]I suggest netpipe-tcp may be the answer. You can get in from synaptic

This package uses a raw TCP protocol to measure network performance.[/QUOTE]

Thanks... I'll try that and let you know how it worked.


-- David

---

### Post by david049 on 2006-05-09
Erm...  how do I use the NetPipe TCP program? :-)

I installed it via Add/Remove Software, but how do I use it?

Thanks

---

### Post by david049 on 2006-05-09
[QUOTE=david049]Erm...  how do I use the NetPipe TCP program? :-)

I installed it via Add/Remove Software, but how do I use it?

Thanks[/QUOTE]


Anybody?

---

### Post by Sendervictorius on 2006-05-10
Not sure, but the description looked promising...

Take a look at the product's web site:
[http://www.scl.ameslab.gov/netpipe/](http://www.scl.ameslab.gov/netpipe/)

---

### Post by danielph on 2006-06-23
You could try netspeed, it's in the repos and documentation is at [http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/](http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/)

Dan

---

### Post by Endolith on 2007-12-13
> **danielph said:**
> You could try netspeed, it's in the repos and documentation is at [http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/](http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/)

Dan

That doesn't tell you the total throughput available; just how much you happen to be using right now.

---

### Post by Endolith on 2007-12-14
Try iPerf.

[http://dast.nlanr.net/Projects/Iperf/iperfdocs_1.7.0.php](http://dast.nlanr.net/Projects/Iperf/iperfdocs_1.7.0.php)

---

