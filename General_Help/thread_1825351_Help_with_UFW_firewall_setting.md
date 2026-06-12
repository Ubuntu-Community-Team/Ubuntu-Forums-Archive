---
title: "Help with UFW firewall setting"
date: 2011-08-15
forum: General Help
---

### Post by Ant01 on 2011-08-15
Please can someone help me with the correct settings for UFW on my Ubuntu Desktop 11.04

I am setting upo a webserver and want the security for hosting websites but I also need to login to the machine via my LAN computers.

I am concerned about setting it up incorrectly and having people hack my machine.

Thanks
:)

---

### Post by haqking on 2011-08-15
> **Ant01 said:**
> Please can someone help me with the correct settings for UFW on my Ubuntu Desktop 11.04

I am setting upo a webserver and want the security for hosting websites but I also need to login to the machine via my LAN computers.

I am concerned about setting it up incorrectly and having people hack my machine.

Thanks
:)

First of all though it can be done and people do, i wouldnt recommend using your Desktop machine as a Web server.

Use another machine if you have it, or a Virtual machine, this is also a good way to limit security issues, or at least concerning your desktop machine.

If it is a dedicated server to which you refer then you are far better running Ubuntu server with Lamp as oppose to desktop ubuntu.

Also UFW is merely a interface to Iptables which is far more configurable command line than using only UFW.

Also is it already behind a firewall such as a router ?

---

### Post by Ant01 on 2011-08-15
Hi Haqking

Thank you for the quick response.

I am new at setting up a website server, you can see my first post at [http://ubuntuforums.org/showthread.php?t=1822365](http://ubuntuforums.org/showthread.php?t=1822365)

To answer your questions;
I have set up a separate server to get to know my way around and therefore am using Ubuntu desktop as a learning curve. I'll migrate to the server addition as I become more familiar with CLI. I use my windows laptop to login via VNC to the ubuntu desktop machine.

I have LAMP installed but would also like to login to Ubuntu desktop so that I can get to know my way around Ubuntu.

The server is behind a router but i'm not sure how to set up the firewall on the router. My knowledge of firewalls is very limited.

I don't understand what you mean by " Also UFW is merely a interface to Iptables"

Thanks

---

### Post by haqking on 2011-08-15
> **Ant01 said:**
> Hi Haqking

Thank you for the quick response.

I am new at setting up a website server, you can see my first post at [http://ubuntuforums.org/showthread.php?t=1822365](http://ubuntuforums.org/showthread.php?t=1822365)

To answer your questions;
I have set up a separate server to get to know my way around and therefore am using Ubuntu desktop as a learning curve. I'll migrate to the server addition as I become more familiar with CLI. I use my windows laptop to login via VNC to the ubuntu desktop machine.

I have LAMP installed but would also like to login to Ubuntu desktop so that I can get to know my way around Ubuntu.

The server is behind a router but i'm not sure how to set up the firewall on the router. My knowledge of firewalls is very limited.

I don't understand what you mean by " Also UFW is merely a interface to Iptables"

Thanks

If you have a router, then the Firewall is probably by default set to deny all incoming.

If you wish to run a Webserver you will need to allow Port 80 on the router for your server.

IPtables is the firewall hard coded into the Linux Kernel (netfilter) and is configured at command line. UFW or GUFW (which is the GUI for UFW) or firestarter etc are merely ways to interact with IPTables.

IPTables command line is more powerful than the said interfaces, so see:

man iptables

for more information.  Also see here [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) from Bodhi on more security related topics pertaining to securing your environment.

---

