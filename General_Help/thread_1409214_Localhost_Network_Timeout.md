---
title: "Localhost Network Timeout"
date: 2010-02-17
forum: General Help
---

### Post by abernut on 2010-02-17
I have a machine running Ubuntu 8.04.

Yesterday I tried adding virtual subdomains, today I removed them after installing VirtualBox.

Now I cant browse any localhost site from the server, Network Timeout. What's weird is I can still hit them from another machine on the network.

Here are the last few lines of my apache2 error log.

[Wed Feb 17 10:31:21 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443
[Wed Feb 17 10:31:21 2010] [notice] caught SIGWINCH, shutting down gracefully
[Wed Feb 17 10:31:32 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Wed Feb 17 10:31:32 2010] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Feb 17 10:39:17 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443
[Wed Feb 17 10:39:18 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443



My /etc/hosts

127.0.0.1       localhost.localdomain    localhost
172.28.159.15   server.name.com  severname
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts

Thank you,
Mike

---

### Post by doas777 on 2010-02-17
hmm. your hosts file is exactly where I would start too, but it looks like it should work.
one thing to try is to put localhost on it's own line with another loopback address like 127.0.1.1.

also can you connect if you supply 127.0.0.1:443 instead of localhost:443?
if not, what is the output of ```
route
``` ? its possible that the route table has the 
loopback route pointing to another gateway (since you are getting 0.0.0.0 as your destination).

---

### Post by abernut on 2010-02-17
made the changes in my hosts file and tried browsing 127.0.0.1:443...No go

Route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.28.159.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.28.159.1    0.0.0.0         UG    100    0        0 eth0

Thank you for your help.

---

### Post by abernut on 2010-02-17
Not sure if this being caused by the issue or causing the issue but....

When I do a restart, I get to my login screen.  After typing in my credientals is hangs for a while. Then an error message pops up.
[B]
error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

---

### Post by abernut on 2010-02-17
Something else that is happening.

When I restart it hangs for a minute then displays 

[B]networkmanager: (WARN)  nm_dbus_init() .........
Make sure the message bus daemon is running[/B]

---

### Post by abernut on 2010-02-17
UPDATE

Everything works fine if I log in with the GNOME Failsafe.

---

