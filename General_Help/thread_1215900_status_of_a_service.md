---
title: "status of a service"
date: 2009-07-17
forum: General Help
---

### Post by burakvarhan on 2009-07-17
hello,

I am using ubuntu 9.04 my question is how to check the status of a service regarding it is running(on) of stopped(off)

particularly I want to be sure that my firewall is on and I dont know a command to check its status

thanks for the replies.

---

### Post by jonobr on 2009-07-17
ps -A 

should list all running processes

The ip_tables module is built into the kernel.
It should run by default when you start up.

to check if the module is loaded you can do a lsmod and look for it in there

Additional , for apps you can go to /etc/init.d and find the program name and usually do a status 

eg

```

/etc/init.d$ ./apache2 status
 * Apache is running (pid 3028).
he@muster:/etc/init.d$ 
```

---

### Post by blueridgedog on 2009-07-17
What do you use for a firewall?

---

### Post by t4thfavor on 2009-07-17
Thats a bad question considering we all use iptables.

---

### Post by blueridgedog on 2009-07-17
> **t4thfavor said:**
> Thats a bad question considering we all use iptables.

Most users use a specific front end to iptables (see [http://swiss.ubuntuforums.org/showthread.php?t=1178988](http://swiss.ubuntuforums.org/showthread.php?t=1178988) for example), each with a different status indication method.  Few new users code iptables scripts by hand and given the commands to list the chains would not be as helpful as showing how to use the interface the original poster is accustomed to.

---

### Post by The Cog on 2009-07-18
Linux has a firewall built into the kernel. It is configured by **iptables** commands. There is no process running to make the firewall happen though, so you can't look in a process list to see of the firewall is configured. If you run the command sudo **iptables -nvL** you will be shown the current firewall rules set. A machine with no rules (all traffic allowed) looks like this:
```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

Rather than use iptables commands directly, most people use a GUI firewall configuration utility such as gufw, firestarter, smoothwall, fwbuilder. These can be used to issue the appropriate commands to iptables, but don't need to be running all the time - only when the rules need changing.

---

### Post by burakvarhan on 2009-07-18
Thank you very much guys. This helped a lot.

---

