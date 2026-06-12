---
title: "Unable to resolve hostname"
date: 2010-12-24
forum: General Help
---

### Post by Ninjin25 on 2010-12-24
Hello,

Doing a search on the forums I can see this is a common topic. However, looking through all the suggestions I'm still stuck with my system displaying user@(none). This could be due to my lack of thorough knowledge of a working linux box. 

Here is everything I have checked so far.

1. Made sure that I am not using underscores
2. Made an entry for 127.0.1.1 for my hostname
3. Trying to start the hostname service provides me with the following error output

> 
sudo: unable to resolve host (none)
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service hostname start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start hostname
start: Job failed to start

4. Trying to do 'restart hostname' I get the following 

> restart: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

4a. The above error may be related to another issue that I'm having with the /var directory.

5. hostname -f gives me 

> hostname: Name or service not known


6. My hostname file looks like

> 
127.0.0.1 localhost
127.0.1.1 ninjin-server1
10.1.10.254 ninjin-server1

Keep in mind that I have tried several other variations of syntax, however I'm not 100% sure on what the correct syntax is for /etc/hostname

7. Here is my /etc/hosts 

> 127.0.0.1       localhost
127.0.1.1       ninjin-server1
10.1.10.254     ninjin-server1
10.1.10.10      ninjin-dell
10.1.10.11      ninjin-laptop
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
~
Questions

1. What is the correct syntax of the /etc/hostname?
2. Are there any obvious problems with what I have shown so far?
3. And of course is there any additional configuration files or anything else I should be concerned about when configuring the hostname of a local machine?

---

### Post by efflandt on 2010-12-25
You should have looked at /etc/hostname before you changed it.  It should normally only contain one hostname (no IP's), but it can either be a simple hostname without any dots, or FQDN (fully qualified domain name, which means hostname.domain).

You can list your hostname for multiple IP addresses in /etc/hosts (which matches hostnames and names, if not in DNS).

Example:
```
efflandt@natty-ssd:~$ **cat /etc/hostname**
natty-ssd

efflandt@natty-ssd:~$ **cat /etc/hosts**
127.0.0.1    localhost    natty-ssd
::1    localhost6    natty-ssd
127.0.1.1    natty-ssd

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```As you found out, your system will have problems if it cannot find its own name.

---

