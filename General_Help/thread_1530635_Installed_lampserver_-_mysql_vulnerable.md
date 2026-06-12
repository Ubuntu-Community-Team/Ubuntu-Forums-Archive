---
title: "Installed lampserver - mysql vulnerable?"
date: 2010-07-13
forum: General Help
---

### Post by J V on 2010-07-13
I installed lampserver and took measures to see that apache would only serve 127.0.0.1 (Which appears to be a software switch as ipconfig says it's port is still "Open")

Mysql however, could be vulnerable: Do I need to secure it or does it only serve localhost? If so, how do I secure it?

---

### Post by robsoles on 2010-07-13
If you have another machine on the network with this one then you can run nmap on this one's IP address and see which ports are reported as being contactable.

If port 80 or 443 (or other ports you may have configured Apache to use) then you haven't sealed HTTP to the localhost.

If port 3306 (not checking self, could be off - Google it yourself) is open to the other machine then MySQL is not sealed to the localhost but just how weak did you make the root password anyway?


If you haven't an alternative machine on the network with you then you could set up a VM in virtualbox or simile using 'bridged' ethernet connection to achieve the same effect as checking from another machine.

---

### Post by J V on 2010-07-14
Is it normal that my computer would be showing 2 ms windows programs open?

```
139/tcp open netbios-ssn
445/tcp open microsoft-ds
```

If I have the wrong IP, what can I run to check the host names of other IPs in the neighborhood?

---

### Post by robsoles on 2010-07-14
Are you running Samba?

Those are 'windows file sharing' ports.


To be sure you are targeting the correct machine you can type ```
ifconfig
```into terminal on the target machine and look for the IP address in the output of the command.

I haven't pursued getting other hostnames in my LAN but: In Ubuntu desktop 'Windows Network' under 'Network' has local workgroups and domains in it, any hosts allowing windows file-sharing will be listed in their workgroup or domain. In Windows same about 'network neighborhood'. Your modem may list active DHCP leases somewhere in it's web interface and that should include hostnames that were reported to it by clients and their IP address as assigned by it.

---

### Post by J V on 2010-07-14
Yes I have samba, and that looks like what's going on... Cool, no ports open but samba, security ftw :P

---

