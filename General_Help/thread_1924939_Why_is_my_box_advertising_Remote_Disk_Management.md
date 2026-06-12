---
title: "Why is my box advertising Remote Disk Management?"
date: 2012-02-13
forum: General Help
---

### Post by street spirit on 2012-02-13
When I run avahi-browse in our office LAN, I see my own host advertising something called "Remote Disk Management":

```
$ avahi-browse -at
...
+   eth0 IPv6 myhostname-2                       Remote Disk Management  local
+   eth0 IPv4 myhostname-2                       Remote Disk Management  local
...
+   eth0 IPv6 myhostname-2 [12:34:56:78:9a:bc]   Workstation             local
+   eth0 IPv4 myhostname-2 [12:34:56:78:9a:bc]   Workstation             local
...
```

The service is marked as local, but I only have a very foggy idea of how Avahi/Zeroconf work, and I'm a bit worried. I'd rather not have my disks managed (or shared) remotely. The thing seems related to the udisks service, of which I also know little, except that it probably helps with automounting removable storage devices.

There is only one entry in /etc/avahi/services - udisks.service:

```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<!-- This file is part of udisks -->

<service-group>
  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_udisks-ssh._tcp</type>
    <port>22</port>
  </service>
</service-group>
```

Should I just (re)move this file? It can't be doing much good anyway, because my sshd is configured to use a different (non-standard) port.

Thanks in advance for any useful advice.

---

### Post by street spirit on 2012-02-17
Anybody?

---

### Post by SwiftTools on 2012-04-20
Yeah anybody? Got the same weird feeling that this is somewhat unwilled and could be harmful.

I'll try to find out what is this service about.

 -Swift

---

### Post by street spirit on 2012-04-20
Just as a quick follow-up for the record: I have removed the config file from /etc/avahi/services in the meantime, and the Remote Disk Management results are gone. I haven't noticed any ill effects, so if you don't need it, it should be safe to remove the file.

---

### Post by SwiftTools on 2012-04-20
It's advertized by 'udisks' (DB disk management) and offer remote disk management:
[http://ubuntuforums.org/showthread.php?t=1500328](http://ubuntuforums.org/showthread.php?t=1500328)
A Ubunutu box (not Kubunutu one) can manage the exposed disks remotely.

 -Swift

---

### Post by mastablasta on 2012-04-20
> **SwiftTools said:**
> A Ubunutu box (not Kubunutu one) can manage the exposed disks remotely.

 
why not Kubuntu one? they use same base the only difference is the Desktop environment.

---

### Post by SwiftTools on 2012-04-20
Indeed, if you read the provided link you'll see that remote-disk-management utility is for GNOME. Not for KDE (AFAIK). Ain't that a Desktop environment difference?

---

### Post by street spirit on 2012-04-20
The "Disk Utility" tool is Gnome only; udisks itself is independent of the desktop environment.

(I only mentioned [kubuntu] because this forum requires me to select a distro variant as part of the title, and I wasn't sure that this setup was really the same for [all variants]).

---

