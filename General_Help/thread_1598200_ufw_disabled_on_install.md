---
title: "ufw disabled on install?"
date: 2010-10-16
forum: General Help
---

### Post by newb85 on 2010-10-16
I just did a clean install of Maverick the other day.  I had done very little with it before installing the Firewall Configuration app for UFW.  Imagine my surprise when the program first opened to show that the firewall was *disabled*.  :(  I'm no expert on networking and security, but I'm pretty sure it's a bad idea to simply have the firewall turned off for no reason.

Prior to that, I *had* installed Apache2 and MySQL, but I hadn't done anything with them yet.  If anything, I would have expected this to open a few ports, but certainly not disable the firewall.

Is there anyone who can explain this.  If for no other reason, I would like to be reassured that the developers haven't taken the *libre *philosophy to extremes at the expense of my security.  (Sorry for the satirical commentary.)

---

### Post by QLee on 2010-10-16
[QUOTE=newb85]...
Is there anyone who can explain this.  If for no other reason, I would like to be reassured that the developers haven't taken the *libre *philosophy to extremes at the expense of my security.  (Sorry for the satirical commentary.)[/QUOTE]
A default install has nothing listening on any port for connection, thus only connections your system initiates will be able to get to you until you choose to start a service listening for a connection. (Simplistic answer.)

For considerably more info on security:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by byStanderone on 2010-10-16
...my ubuntu experience started from gutsy, tho my latest install is lucid, and had observed that ufw is disabled by default after installing it...and i accept the fact that there should be the element of trust to the devs, but i make it a point not to be online during any installation...and enables ufw before anything else.

---

### Post by donato roque on 2010-10-18
you will find that the installation configuration of the ubuntu "firewall" is the same as the default config of ufw (deny all incoming, allow outgoing).  Check this out.

With ufw disabled, go to [grc.com]("http://www.grc.com") website that evaluates your firewall.  You will have the same results as with an enabled ufw with defaults.

The ubuntu devs have all ports closed (not listening) so any connection you get is initiated from inside.  So what's the difference when you enable ufw?  none.  Unless you run a server software that opens ports and listens for connections.  Then you will be advised to configure your "firewall" to plug what you open.  The devs assume that you know what you are doing.

---

### Post by ankspo71 on 2010-10-18
Hi,
> **newb85 said:**
> 
Prior to that, I *had* installed Apache2 and MySQL, but I hadn't done anything with them yet.  If anything, I would have expected this to open a few ports, but certainly not disable the firewall.

Believe it or not, I once asked the same question here a couple of years ago. When I used Windows, I practiced high security, but now that I am a Linux user (and have gotten to know more about it), I am more comfortable about security in Linux. 

In windows, unless there is a firewall turned on and properly set, inbound and outbound connections are both allowed. If we want a windows machine secured, we have to turn off all inbound connections that aren't going to be needed by the system, and possibly some of the outbound connections too for safe measures.

Linux (by default) is quite the opposite... there are no inbound connection exceptions, so only outbound connections can be made. Linux is already secured in terms of 'firewalling' whether or not the firewall is turned on, but what we need to do sometimes is open an inbound port for a specific application to listen on (eg: a server of sorts or maybe a game that can network players together etc) so people on the internet to be able to connect to our computers on their own free will. By default they can't connect to us.

Also, If I understand correctly, I think Linux is little more immune to port scanning and other attacks too, not only because we don't accept incoming connections, but also because by default our IPtables are designed to not send back reject messages, so it appears as if we don't exist, "stealth mode". We do need to be careful about opening ports though. For 'Deny' vs 'Reject' See: [https://help.ubuntu.com/community/Gufw#Adding%20Rules](https://help.ubuntu.com/community/Gufw#Adding%20Rules)

We generally don't need to open ports to share (seed) with our torrent clients either, because the torrent clients are capable of both downloading and sharing files on an outbound connection only. This might or might not apply to other 'p2p' downloading/sharing methods though.

Hope this helps.

---

