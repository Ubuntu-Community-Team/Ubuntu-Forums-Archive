---
title: "Error: Failed to connect to NBD server"
date: 2011-01-28
forum: General Help
---

### Post by fieldyweb on 2011-01-28
I'm going slightly out of my mind here, because there are so many half solved blog and forum posts about this, but none seem to answer my issue:

I am using VMware to host an Edubuntu 10.10 server with LTSP enabled 
I must note at this point that this issue also occurs with the 10.04 Alternate install, the 10.10 Ubuntu Desktop install with packages from the repos and only works on 9.04 so far.

Having installed Edubuntu, and booted my PXE client, also a VM on the same network as my 2nd statically addressed NIC, i am able to see that the PXE is working, and i get as far as the 10.10 splash screen is working.  then i get a busy box error with the message

Error: Failed to connect to NBD server

So i found the following Forum post maked Solved, Its not
[http://ubuntuforums.org/showthread.php?t=1473451](http://ubuntuforums.org/showthread.php?t=1473451)

None of this works

I have also tried this

[http://www.rickogden.com/2010/06/ltsp-part-2-configuration/](http://www.rickogden.com/2010/06/ltsp-part-2-configuration/)
After the break mount section


What have i noted so far?

If i run /etc/init.d/nbd-server stop then start, the server dies with a Nothing to do error message as it cannot find its config file

I cannot see any log files which might shed any light on this..

Can anyone out there shed some light as to what i might be doing wrong, as an out of the box installation, im suprised to be having this issue.

Also if 10.10 doesn't work, can i sue a 10.04 Ubuntu image booted from a 9.04 Ubuntu LTSE server? If so, i will go down that route.. 

As always URL's, directions, helpful, and i will feedback all that is needed.

---

### Post by fieldyweb on 2011-01-29
Bump???
Really, no one.. are am i surrounded by ex Windows owners moaning that Ubuntu ins't like XP?

---

### Post by gottr on 2011-02-10
Sometime with my system it just happens and a restart of the client will then connect.  If that doesn't work then rebuild the client image via ltsp-build-client via command line on the server.

---

### Post by abpriest on 2011-02-17
fieldyweb,

Did you figure this issue out? I installed ubuntu 10.10 two days ago and I am having the same problem. 

I'm going to try ltsp-build-client tomorrow, but I'd like to know more about how the system works.

---

### Post by Mibble on 2011-02-23
my problem happened after i updated ubuntu updates.  i am using 10.10 and the linux build client did not work. i even tried a sleep mode prior to the mounting to no avail.

---

### Post by trippedn on 2011-07-04
Old thread, but relevant information:

Try seeing if the nbdserver is even running and listening through inetd:
```
netstat -tlnp
```
You should see something similar to the following:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      16461/inetd

```
Here you will notice that inetd is listening on port 2000.

Some packages will remove inetd (package name: openbsd-inetd) and install xinetd which will prevent your clients from booting (for example: vnc server). In this case, I would recommend checking your dpkg log (/var/log/dpkg.log and any other logs that may have been log rotated) for information regarding inetd (install/remove etc).

EDIT: This occurred because someone installed vnc4server and it broke all of our clients :(

---

### Post by captaintrav on 2012-03-26
I had this problem, and I'm purposely running xinetd for vncserver previously.  Xinetd reads the inetd.conf and tries to run these services as well for compatibility reasons. Looking at the logs, though (I believe daemon.log), xinetd disables these services because there are no matching named entries in /etc/services.  The nmbserver in inetd.conf is *named* 2000, which is just the port number.  Inetd seems fine with this, but xinetd is not.  Xinetd doesn't know what port to run the service on.  The inetd.conf entry is supposed to be the service *name*, and the port to listen on is configured in /etc/services, or at least that's what xinetd expects when running with inetd compatibility on.

My fix is to add the services with the port number being the service name to /etc/services:

```
# Local services
2000            2000/tcp
9571            9571/tcp
9572            9572/tcp

```

Now we have a service "named" 2000 that runs on port 2000.  Now ltsp runs happily on Ubuntu 10.04 using xinetd for me, easy fix.  Old thread, but if someone finds this with google like I did, maybe it will help them.

---

