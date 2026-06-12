---
title: "Ubuntu apt-get update problems"
date: 2011-07-08
forum: General Help
---

### Post by nascent on 2011-07-08
Hi, I've been getting errors updating remote server I connect to via ssh.  From what I understand if I remove the ubuntu-desktop meta package it will fix this error but also remove ssh, which I need in order to reconnect back to my server.  I'm really not keen on reinstalling ubuntu.

Any help would be much appreciated.

Here is the aptitude update and safe-upgrade log:

> Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initialising package states...
Building tag database...
The following packages have been automatically kept back:
  firefox-3.0 libbind9-30 libdns35 libisc35 libisccfg30 liblwres30 
The following packages have been kept back:
  bind9-host dnsutils firefox-gnome-support linux-headers-generic 
The following partially installed packages will be configured:
  acpi-support acpid powermanagement-interface ubuntu-desktop 
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...       [80G acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...       [80G Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initialising package states...
Building tag database...


---

### Post by Bucky Ball on 2011-07-08
Have you tried:

```
sudo apt-get update
```... followed by:

```
sudo apt-get upgrade
```? That won't upgrade the OS release, only the packages that need it. Similar to what you are doing but never know ...

---

### Post by bapoumba on 2011-07-08
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/63450](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/63450)

Just out of curiosity, which ubuntu release is your server running on ?

---

### Post by nascent on 2011-07-09
Yeah I used to use apt-get but that doesn't work either.  I'm using 8.04.4.

I followed the various 'fixes' in your link and none have helped.

---

### Post by 11ghjones on 2011-07-09
I would try a:

```
sudo apt-get purge acpi-support acpid powermanagement-interface ubuntu-desktop 
```

Followed by a:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by 11ghjones on 2011-07-09
And removing the ubuntu-desktop metapackage should not remove ssh.  I don't know who told you that.

---

### Post by Bucky Ball on 2011-07-10
8.04 LTS is no longer supported. You may fix a few of your issues by upgrading to a supported release. In Update Manager you should see 'New LTS release available' or something like that up the top. That will upgrade you to the next LTS release, 10.04, supported until 2013, in a couple of clicks. Using this method (rather than a clean install) keeps all installed programs and settings, but I would still backup your /home partition or directory.

---

### Post by nascent on 2011-07-10
> **11ghjones said:**
> And removing the ubuntu-desktop metapackage should not remove ssh. I don't know who told you that.
Ok thanks for letting me know, I was under the impression letting ubuntu-desktop be removed would be a bad thing.  if my server wont start after a reboot then I basically lose everything.

> **11ghjones said:**
> ```
sudo apt-get purge acpi-support acpid powermanagement-interface ubuntu-desktop 
```Followed by a:

```
sudo apt-get install ubuntu-desktop
```
I tried this and it didn't resolve my problem.
I still get: 
```

Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```> **Bucky Ball said:**
> 8.04 LTS is no longer supported
This is a whole other issue.  I've tried updating ubuntu and it states I haven't got enough free space on / so I'll worry about that issue in the future I think and concentrate on getting this problem solved first.

---

### Post by Bucky Ball on 2011-07-10
Just my point. You might not be able to get your current problem fixed on an unsupported release ... but then, you might ...

---

### Post by nascent on 2011-07-11
Any time I've tried updating it says I need over 3gb more free space on /

I've removed large packages, and made sure only one copy of the kernel exists, and still i've only got 500mb free.  So there's not much I can do about it, it's a remote server so I can't do anything.

---

### Post by Bucky Ball on 2011-07-11
> **nascent said:**
> Any time I've tried updating it says I need over 3gb more free space on /

Upgrading you mean? Yea, know that problem. Not enough headroom on the partition you are trying to upgrade so impossible to do that way. Don't bother trying to make space. Clean install for you, unless you can shrink one of the partitions next to the / partition and expand the / partition into the free space you've created. I have a desktop which has exactly the same issue and clean install on that one when I get around to it. ;)

---

