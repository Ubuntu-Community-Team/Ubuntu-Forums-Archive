---
title: "thin client can't boot LTSP???"
date: 2006-03-29
forum: General Help
---

### Post by jgregory on 2006-03-29
Just installed Edubuntu 5.10. Updated it. Configured my DHCP. My thin clients start to load the OS and then I get...

    mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory 
    mount: Mounting /dev on /root/dev failed: No such file or directory 
    Target filesystem doesn't have /sbin/init

    /bin/sh: can't access tty; job control turned off

Any ideas what I'm missing?

---

### Post by chibilink on 2006-04-20
I am having this same problem as well. Has anyone else figure out how to get around this? Thin Client was loading, I started having this problem after i rebooted the server.

---

### Post by jgregory on 2006-04-21
I couldn't get Edubuntu to work. I installed Ubuntu and got LTSP up and running. I followed the LTSP install instructions for Ubuntu at [https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto) 

I'm sure Edubuntu can work, I just couldn't figure it out.

Hope that helps. Good luck. 

John

---

### Post by jgregory on 2006-04-21
I just looked over my notes. I had the same problem with the Ubuntu installation at first. I had to change the root path designation on my DHCP server. I had the root path designated as xxx.xxx.xxx.xxx:/opt/ltsp/i386 and I changed it to /opt/ltsp/i386  Basically I got rid of the IP address at the start.

I'm running a separate DHCP server (Windows 2000) instead of running one on the Ubuntu server. If this doesn't make since, say so, and I'll explain in greater detail.

Good luck.

John

---

### Post by chibilink on 2006-04-21
Currently the Machines that I have set up as thin clients, do not have any other OS software on them. I've tried reinstalling Edubuntu 5.10 two sperate times to no sucess. I just for the life of me can't figure out what changed, that allowed the Thin Clients to boot to the LTSP the first time, that isn't letting it boot up this time after i made that first server restart. I will try and retrace all the steps that I have taken and keep you posted if I have made any progress.

---

### Post by chibilink on 2006-04-21
Fixed it!!

The problem turned out to be the fact that I was using a router. It appears that the routers DHCP service was conflicting with my servers and that was causing the error mentioned above. I swapped out the router for just a regular 10/100 hub, and everything is working perfectly.

---

### Post by _linux_ on 2006-04-21
I'm also using Edubuntu, but not the LTSP version, the normal one. :KS

---

### Post by a5benwillis on 2007-02-13
I'm having the same problem but I'm using a novell dhcp server. Has anyone else found a solution to the job control turned off error?


Ben

---

