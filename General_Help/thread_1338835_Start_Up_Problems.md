---
title: "Start Up Problems"
date: 2009-11-26
forum: General Help
---

### Post by dashpilot79 on 2009-11-26
I'm running 9.04 everything was working fine untill i decided to play around with IPTABLES.  I set the default rules on INPUT, OUTPUT and FORWARD to Deny now BIND9 will not stop and NFS gives me a mounting error.  Any thoughts?

Dashpilot79

---

### Post by blueridgedog on 2009-11-26
A default rule to deny for all actions, without a prior rule for accepting the traffic will deny all traffic.  You need to build in rules to accept the traffic you want before issuing the deny rule.

---

### Post by cariboo on 2009-11-26
Have a look [here]("http://ubuntuforums.org/showthread.php?t=510812"), towards the bottom of the page there is information on iptables.

---

### Post by blueridgedog on 2009-11-27
Excellent links are included there.  

If you search the web for iptables examples you will find many that go over the process of setting a default rule, flushing the tables, then building accept then drop rules.

Here is one:

[http://oceanpark.com/notes/firewall_example.html](http://oceanpark.com/notes/firewall_example.html)

---

### Post by dashpilot79 on 2009-12-06
I figured it out, you have to open port 953 on the local interface for Bind9 to run.

---

