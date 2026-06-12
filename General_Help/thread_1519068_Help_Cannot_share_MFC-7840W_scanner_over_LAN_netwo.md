---
title: "Help: Cannot share MFC-7840W scanner over LAN network"
date: 2010-06-27
forum: General Help
---

### Post by golbez_88rule on 2010-06-27
I've completed a fresh installation of Ubuntu Lucid and I have sucessfully installed the drivers for my Brother MFC-7840W printer/scanner combo. I've verified that printing and scanning both work perfectly fine from the Ubuntu PC.  Running Simple Scan works just fine, and I made the necessary tweak to make sure that any user can run the scanner and not just the root user.  I would like to share this over the network so that my other computers can use the scanner, but all of my attempts have failed.  The ip address of the ubuntu machine is 192.168.1.2. I've consulted various posts and how-tos, and here are all of the steps I have taken:

1. Installed the xinetd package
2. Created a file ```
/etc/xinetd.d/sane
``` with the following contents:

```

service sane
{
   socket_type = stream
   server = /usr/sbin/saned
   protocol = tcp
   user = saned
   group = saned
   wait = no
   disable = no
}

```

Note that I have also tried having ```
user=root
``` and ```
group=root
``` and no success

Also, one of the forum posts recommended I add the user saned to the group scanner. I do not have any group called scanner, but I do have a group called saned.  So I ran the command ```
sudo adduser saned saned
``` in case that would help.

3. Edited the file called ```
/etc/default/saned
``` to match the following:

```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes
# Set to the user saned should run as
RUN_AS_USER=saned

```

4. Edited the file ```
/etc/sane.d/saned.conf
``` and added the range of IP addresses for the machines on my network I want to have access:

```

# saned.conf
# Configuration for the saned daemon

## Daemon options
# Port range for the data connection. Choose a range inside [1024 - 65535].
# Avoid specifying too large a range, for performance reasons.
#
# ONLY use this if your saned server is sitting behind a firewall. If your
# firewall is a Linux machine, we strongly recommend using the
# Netfilter nf_conntrack_sane connection tracking module instead.
#
# data_portrange = 10000 - 10100


## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
localhost
192.168.1.1/200
#192.168.0.1/29
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and
# /etc/services must also be properly configured to start
# the saned daemon as documented in saned(8), services(4)
# and inetd.conf(4) (or xinetd.conf(5)).

```

I have tried to restart saned using ```
sudo invoke-rc.d saned restart
``` after these tweaks but I get the following error:

```

Restarting SANE network scanner server: invoke-rc.d: initscript saned, action "restart" failed.

```

However I do not receive any errors after restarting xinetd with ```
sudo /etc/init.d/xinetd restart
```

I must be pretty close, but missing something. Anyone have any ideas?

---

### Post by cariboo on 2010-06-27
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=679028") tutorial.

---

### Post by Leppie on 2010-06-27
> **cariboo907 said:**
> Have a look at [this]("http://ubuntuforums.org/showthread.php?t=679028") tutorial.
i really doubt that tutorial is of any help...
> **golbez_88rule said:**
> Also, one of the forum posts recommended I  add the user saned to the group scanner. [COLOR=Red]I do not have any group called  scanner[/COLOR], but I do have a group called saned.  So I ran the command  ```
sudo adduser saned saned
``` in case that would help.

and this is from the tutorial:
> 3. Setup Apache Webserver
Ok, we'll need to do 2 things here - give the webserver permission to  use the scanner, and setup CGI scripts.

To give the webserver permission to use the scanner, run:
```
sudo adduser www-data [COLOR=Red]scanner[/COLOR]
``` 


---

### Post by Leppie on 2010-06-27
what you really have to do, is edit the /etc/sane.d/net.conf on the client machines and add the ip address of the machine acting as scan server at the end of the file, so it looks something like this (amend the ip address as needed):
```
# This is the net backend config file.

## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60

## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost
192.168.1.1
```

ps: saned now is an upstart job.


EDIT: i had not noticed before, but you need to set the run-as user to root in the /etc/default/saned file on the scanner server:
```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes
# Set to the user saned should run as
RUN_AS_USER=saned

```

---

### Post by golbez_88rule on 2010-06-27
> **Leppie said:**
> what you really have to do, is edit the /etc/sane.d/net.conf on the client machines and add the ip address of the machine acting as scan server at the end of the file, so it looks something like this (amend the ip address as needed):
```
# This is the net backend config file.

## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60

## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost
192.168.1.1
```

ps: saned now is an upstart job.


EDIT: i had not noticed before, but you need to set the run-as user to root in the /etc/default/saned file on the scanner server:
```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes
# Set to the user saned should run as
RUN_AS_USER=saned

```

Thanks Leppie. I've made the following modifications based on your advice.  First, I changed /etc/xinetd.d/sane to this:

```

service sane
{
   socket_type = stream
   server = /usr/sbin/saned
   protocol = tcp
   user = root
   group = saned
   wait = no
   disable = no
}

```

Next I added the following to the client's /etc/sane.d/net.conf file:
```

# localhost
192.168.1.2

```

Where 192.168.1.2 is the IP of the scan server. Finally I changed /etc/default/saned to the following:

```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes

# Set to the user saned should run as
RUN_AS_USER=root

```

I am still getting the same error when I execute sudo invoke-rc.d saned restart as in my first post, so it seems that the saned process is not running.  FWIW, when I go to Users and Groups, I see that the saned group only has my username (eric) listed (although the box is unchecked) and not the root user.

---

### Post by Leppie on 2010-06-28
first i would remove xinetd package and the /etc.xinet.d/sane file, you don't need them at all.
as i stated before, saned is an upstart job and can be (and should be) controlled like this:
```
sudo service saned start|stop|restart
```

i just rewrote the scanner howto, as it was not applicable for lucid lynx.
you can find my version here: [http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network](http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network)

i'm currently working on the web interface part.

---

### Post by golbez_88rule on 2010-06-28
> **Leppie said:**
> first i would remove xinetd package and the /etc.xinet.d/sane file, you don't need them at all.
as i stated before, saned is an upstart job and can be (and should be) controlled like this:
```
sudo service saned start|stop|restart
```

i just rewrote the scanner howto, as it was not applicable for lucid lynx.
you can find my version here: [http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network](http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network)

i'm currently working on the web interface part.

Success! I was able to start the saned process with your command and also I changed the way I wrote the IP addresses of the computers on the network in the /etc/sane.d/saned.conf to the following:
```

#scan-client.somedomain.firm
#localhost
#192.168.1.1/200
192.168.1.4
192.168.1.7
192.168.1.100
#192.168.0.1/29
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

```

Now I am able to use xsane on the client computers (one is crunchbang 8.04 and the other WINXP) to scan over the network. I was not able to get it to work with the range of IP addresses defined, but at least listing the individual IP addresses like above works. Thank you for putting together the great scanner howto!

---

### Post by Leppie on 2010-06-29
you're welcome.
glad it's working now :)

---

### Post by ihristov on 2011-03-09
The address you have below is incorrect. That's why the "group" does not work.

If you want to allow anybody in 192.168.1.xxx to have access, you should specify it like so
```
192.168.1.0/24
or
192.168.1.0/255.255.255.0

```
You can use an "IP address calculator" like [http://jodies.de/ipcalc](http://jodies.de/ipcalc) to make sure your notation is correct.

> **golbez_88rule said:**
> Success! I was able to start the saned process with your command and also I changed the way I wrote the IP addresses of the computers on the network in the /etc/sane.d/saned.conf to the following:
```

#scan-client.somedomain.firm
#localhost
#192.168.1.1/200
192.168.1.4
192.168.1.7
192.168.1.100
#192.168.0.1/29
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

```

Now I am able to use xsane on the client computers (one is crunchbang 8.04 and the other WINXP) to scan over the network. I was not able to get it to work with the range of IP addresses defined, but at least listing the individual IP addresses like above works. Thank you for putting together the great scanner howto!

---

