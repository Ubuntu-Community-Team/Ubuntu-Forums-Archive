---
title: "how to iperf"
date: 2012-08-17
forum: General Help
---

### Post by qwertyjjj on 2012-08-17
I need to perform some network tests with iperf.
Do I need to install this on a server as well?
Do I need to open ports to run these tests?

Also, I would like to chekc the connection when connected and disconnected via VPN can I simply run it from the command line for either connection?

---

### Post by aromo on 2012-08-17
> **qwertyjjj said:**
> I need to perform some network tests with iperf.
Do I need to install this on a server as well?
Do I need to open ports to run these tests?

Also, I would like to chekc the connection when connected and disconnected via VPN can I simply run it from the command line for either connection?

Download jPerf from sourceforge.net (I think 2.0.2 is the most recent version).  It's a Java-based GUI for iPerf that works on both ends (server and client).

---

### Post by qwertyjjj on 2012-08-17
I have used iperf to test speed from a client to my server.
I now need to test the speed from the server to my client but it just times out, presumably no ports are forwarded on my client side router, etc.
Is the a public iperf server I can use instead?

On my client, I go to [www.speedtest.net](www.speedtest.net) and get 30Mb/s
However, on using iperf to the server I only get 2Mb/s so something is wrong and I don;t know if it is the server or just the ISP connection to the server.

---

