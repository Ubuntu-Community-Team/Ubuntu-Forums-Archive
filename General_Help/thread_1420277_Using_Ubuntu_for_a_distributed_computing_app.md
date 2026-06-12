---
title: "Using Ubuntu for a distributed computing app?"
date: 2010-03-02
forum: General Help
---

### Post by Marcus Green on 2010-03-02
Hello.

I have a rather basic question regarding Ubuntu. I'm not really looking for a walkthrough, but rather, a bit of help with Ubuntu itself and choosing the right platform for my needs.

I'm in the process of developing an application that will need to make use of some heavy processing power, and am looking into various ways to distribute the load across multiple machines.

The mechanics of the application are quite simple. The application operates on a large number of work units, and is called from the command line. To invoke the application, I run a simple:
```

wurun --in=00000001.wu --out=00000001.res

```I built the application like this to make for easy distribution of the calculations, but I'm a bit fuzzy on how to distribute them.

Going in, I thought I'd just use a simple LAMP platform to wrap shell_exec commands running each instance of wurun, but then I got to thinking that Linux has made great headway in cloud computing and distributed applications.

Is Ubuntu suitable for distributing a load like this?

The application will be run across a wide variety of computers, with different specs, much like JBOD RAID is to hard drives.

Is the Ubuntu cloud platform what I should be looking at, or is there a simpler way of doing this?

Advantages of DC:

[LIST]
[*]Even distribution of work units
[*]Maximization of each CPU's individual capacity
[*]Automatic CPU load balancing
[*]Ease of bringing new nodes online
[/LIST]


Advantages of LAMP wrapper:

[LIST]
[*]Ease of setup
[*]Potentially less overhead
[/LIST]


Basically, my question is this: does the Ubuntu platform offer a simple way to distribute CPU-intensive tasks across a diverse array of computers, with an easy mechanism to add new computers to the cluster, or are the Ubuntu/Linux DC capabilities instead designed for enterprise-grade applications that focus on reliability, not even distribution of work across dissimilar hardware?

Of particular importance is the ability to install the OS, the DC client, and bring the node into the cluster with minimal reconfiguration, and automatic load balancing, as opposed to the LAMP wrapper, which would require manual benchmarking, tedious configuration edits, etc.

Thank you all for your help and in producing such a great and free Linux distro.

---

### Post by Marcus Green on 2010-03-03
Anyone?

---

