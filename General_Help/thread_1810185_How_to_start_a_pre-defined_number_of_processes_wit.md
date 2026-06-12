---
title: "How to start a pre-defined number of processes with Upstart"
date: 2011-07-22
forum: General Help
---

### Post by chrisotherwise on 2011-07-22
Hello,

I have a daemon that needs to be spawned a certain number of times. The actual number is determined by looking in a configuration file. 

I would very much like to run and supervise the daemon using Upstart, but I can't see any obvious way of telling Upstart to run exactly a certain number of instances of a script.

I've read about Upstart "instance" processes, and can see how you could run as many copies of a process as you want by doing something like:

start my_service_daemon id1
start my_service_daemon id2
start my_service_daemon id3
start my_service_daemon id4

... but I can't work out how to get Upstart to do that automatically and run exactly 4 copies of the daemon itself. Is such a thing possible?

Thanks.

---

