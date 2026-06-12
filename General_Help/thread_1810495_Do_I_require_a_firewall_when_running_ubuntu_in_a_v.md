---
title: "Do I require a firewall when running ubuntu in a virtual box?"
date: 2011-07-23
forum: General Help
---

### Post by donthaveacow on 2011-07-23
Hey everyone, so the title pretty much says it all: do I need to have a firewall while running ubuntu in a virtual box? I have Zone Alarm on my Windows 7 host, and was wondering if this is sufficient?

Thanks in advance!

---

### Post by lmarmisa on 2011-07-23
No, you do not need any firewall in your host while you run Ubuntu in VirtualBox. But If you have ZoneAlarm, give permissions to VirtualBox to allow the access to the network.

---

### Post by donthaveacow on 2011-07-23
Sorry I meant the other way round. Do I require a firewall in the guest (ubuntu in this case)? If so, how do I install one? I only just installed ubuntu tonight and have never used it before so am pretty lost!

---

### Post by lmarmisa on 2011-07-23
> **donthaveacow said:**
> Sorry I meant the other way round. Do I require a firewall in the guest (ubuntu in this case)? If so, how do I install one? I only just installed ubuntu tonight and have never used it before so am pretty lost!

The same answer again. You do not need any firewall.

Anyway, this link shows information about the optional firewall of Ubuntu:

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

VirtualBox connects the VM to the network using the NAT mode as default. If you wish to connect your VirtualMachine to you LAN as any other physical computer select the mode Bridged Adapter in the Network settings of your virtual machine.

Best regards,

Luis

---

### Post by donthaveacow on 2011-07-23
Ok, thanks for the help!

---

