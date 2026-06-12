---
title: "Connecting to a Remote  Server from Ubunto using theTerminal Server facility"
date: 2010-07-04
forum: General Help
---

### Post by ravikswamy on 2010-07-04
Dear Forum members
 
Very recently we have shifted from Windows XP (SP2) Operating System to Ubuntu10.04. We have around 300 systems (client side) running on Ubuntu now.
 
Our ERP application is developed on VB (front end) and SQL 2008 (backend). Our central server is at Chennai. Hitherto the client systems were connecting to the central server through dedicated leased lines using the Remote Desktop connection facility with a static IP. We have 1 Mbps leased line facility connecting the various centres. We were experiencing no problems in connecting to the Server till now.
 
However on shifting from Windows XP (SP2) OS to Ubunto 10.04, connectivity has become a major issue. All client systems are complaining that the Remote Terminal Access facility in Ubunto is 1/4th the speed of the erstwhile Windows platform. There has been a widespread demand to go back to Windows - a move we are resisting up till now. However the fact remains that connection to our central server through the Ubuntu Remote Terminal Access is abysmally slow.
 
Database Server configuration: IBM Xeon Hexacore Dual Processor with RAID 5 - 32 GB RAM
VB Front End Server : !BM XEon Dual Process Hexacore with RAID 5 - 22 GB RAM
 
Client Systems : Minimum 512 MB RAM : Intel / AMD Processors : Min 80 GB Hard disk running Ubunto 10.04
 
**Any guidance on how this can be speeded up ? Or have we missed something during the configuration of Ubuntu 10.04 ?**
 
We will be extremely thank for some VERY URGENT HELP.
 
With Regards to the Ubuntu Forum Community
Ravi

---

### Post by dcstar on 2010-07-04
> **ravikswamy said:**
> Dear Forum members
 
Very recently we have shifted from Windows XP (SP2) Operating System to Ubuntu10.04. We have around 300 systems (client side) running on Ubuntu now.
 
Our ERP application is developed on VB (front end) and SQL 2008 (backend). Our central server is at Chennai. Hitherto the client systems were connecting to the central server through dedicated leased lines using the Remote Desktop connection facility with a static IP. We have 1 Mbps leased line facility connecting the various centres. We were experiencing no problems in connecting to the Server till now.
 
However on shifting from Windows XP (SP2) OS to Ubunto 10.04, connectivity has become a major issue. All client systems are complaining that the Remote Terminal Access facility in Ubunto is 1/4th the speed of the erstwhile Windows platform. There has been a widespread demand to go back to Windows - a move we are resisting up till now. However the fact remains that connection to our central server through the Ubuntu Remote Terminal Access is abysmally slow.
........
**Any guidance on how this can be speeded up ? Or have we missed something during the configuration of Ubuntu 10.04 ?**
.........
On one Ubuntu test box try one or all of these:
[LIST=1]
[*]Disable IPv6
[*]Reduce the MTU in the networking options
[*]Use a different app like the Terminal Server Client (tsclient).
[*]Change default options in the client to reduce bandwidth requirements.
[/LIST]

---

