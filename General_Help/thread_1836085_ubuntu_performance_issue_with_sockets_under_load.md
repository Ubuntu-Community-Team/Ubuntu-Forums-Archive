---
title: "ubuntu performance issue with sockets under load"
date: 2011-08-30
forum: General Help
---

### Post by deanhiller on 2011-08-30
On a highly overloaded server(we are running load on purpose), we see these pauses for 2 to 30 seconds where the code does nothing.  We used a JVM server at first but then reproduced it with a echo server written in C and had the same issue.  I believe that the NIC should still feed through packets and just drop more on the floor...that would be fine, but it doesn't seem to be doing this.

So here are the top things we noticed DURING these long pauses
1. cpu goes to ZERO
2. packet loss starts occuring at that freeze(we believe it is a symptom not cause based on analyzing)
3. thread dumps in java 6 seconds apart are exactly the same using diff tool except one line...the date!!
4. adding more clients make the pauses happen sooner and LONGER
5. telnet into the same port HANGS during the pause
6. telnet into other ports works FINE!!!
7. lsof command hangs during the pause while other commands do not hang
8.  When I have 2 clients, 2 servers I do not see the issue but I see the issue more with 6 client, 6 servers(I find this odd as we can see the load was distributed evenly)
9. I easily see the issue when I have more clients than servers to really overload it on purpose...and I would expect some degredation but not expect the CPU to go to ZERO.

Any ideas on what is going on?  It is like the linux drivers are not built correctly to work if we have a traffic spike....during that traffic spike, instead of processing the same rate without the spike, we will actually tank...I might expect a small drop in performance but not to tank like what I am seeing where we have huge long pauses.

thanks,
Dean

---

### Post by jlukescott on 2012-02-19
Could you copy & paste the dumps you are getting?

---

### Post by deanhiller on 2012-03-03
it turned out to be a specific JVM issue that is only reproducible if you are under very high load so slamming 20 servers, only about 2 servers show the issue each time.  switching to another JVM fixed it I finally found out(but had lost this post).

---

