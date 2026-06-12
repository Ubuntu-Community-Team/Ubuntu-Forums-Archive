---
title: "Kubuntu firewall???"
date: 2006-06-02
forum: General Help
---

### Post by iMac on 2006-06-02
I just installed Kubuntu the new 6 version, i do not see any form of firestarter or firewall in the add and remove programs like in previous versions. Do i need a firewall??? 
Thanks,
Mike

---

### Post by Dr. Nick on 2006-06-03
Linux has a firewall built in, All firestarter is is a GUI to configure it. I dont have kde right now but seem to remember a firewall config in the kde control center

---

### Post by hvbakel on 2006-06-03
If you're looking for an easy firewall configuration utility for kde, try guarddog (available in the repositories).

---

### Post by abloylas on 2006-06-04
I just installed firestarter using adept on kubuntu dapper. No icon appeared in the main menu. This is what i get when trying to run from the command line for the first time. What gives?

abloylas@marvin:~$ sudo firestarter
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error reading file /etc/firestarter/inbound/allow-from: No such file or directory
Error reading file /etc/firestarter/inbound/allow-service: No such file or directory
Error reading file /etc/firestarter/inbound/forward: No such file or directory
Error reading file /etc/firestarter/outbound/deny-to: No such file or directory
Error reading file /etc/firestarter/outbound/deny-from: No such file or directory
Error reading file /etc/firestarter/outbound/deny-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-to: No such file or directory
Error reading file /etc/firestarter/outbound/allow-from: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
/bin/sh: /usr/bin/esd: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Warning: External interface previously configured not found
Warning: Internal interface previously configured not found

---

