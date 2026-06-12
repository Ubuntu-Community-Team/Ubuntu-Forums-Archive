---
title: "Samba with WINS and cross-subnet browsing over VPN WAN"
date: 2009-11-06
forum: General Help
---

### Post by Craig1972 on 2009-11-06
[FONT=Times New Roman]I am trying to get cross-subnet browsing working. I have samba configured as a WINS server. The WINS server is also the local master browser (LMB) as well as the domain master browser (DMB) for my workgroup. This WINS server is in subnet 1 [/FONT]
 
[FONT=Times New Roman]I have only two subnets. These subnets are joined via a WAN point-to-point VPN connection (OpenVPN). All the computers in both subnets are in the same workgroup called 'WORKGROUP'. [/FONT]
 
[FONT=Times New Roman]Subnet 1 = [[COLOR=#0000ff]192.168.1.0/24[/COLOR]]("http://192.168.1.0/24")[/FONT]
[FONT=Times New Roman]Subnet 2 = [[COLOR=#0000ff]192.168.3.0/24[/COLOR]]("http://192.168.3.0/24")[/FONT]
[FONT=Times New Roman]VPN Subnet = [[COLOR=#0000ff]192.168.2.0/24[/COLOR]]("http://192.168.2.0/24")[/FONT]
 
[FONT=Times New Roman]Routing is working and all computers on each subnet can ping each other. All the Netbios ports are open in the firewall and all computers can browse each other's shares. [/FONT]
 
[FONT=Times New Roman]The problem I am having is the browse list is not complete and not all computers are showing up in the network neighbourhood. [/FONT]
 
[FONT=Times New Roman]It seems none of the PC's in subnet 2 appear in the browse list of computers in subnet 1...and none of the PC's in subnet 2 appear in the browse list of subnet 1.  [/FONT]
 
[FONT=Times New Roman]Any advice appreciated. [/FONT]
 
[FONT=Times New Roman]Thanks,[/FONT]
 
[FONT=Times New Roman]Craig[/FONT]

---

### Post by Craig1972 on 2009-11-06
Question should a windows based PC (Vista and XP) operating as a LMB be able to sync browse lists with a DMB PC that is running Ubuntu (samba 3.4.0)....
 
 
Craig

---

### Post by Craig1972 on 2009-11-06
Some more testing.  If I stop the 'Computer Browser Service' on the LMB of subnet 2 and no other PC's are running on subnet 2 then it looks like PC uses the DMB for the browse list (ie the Ubuntu box)  
 
So here we have 'beth-pc' as the LMB and it is the only computer running in subnet 2.  The browse list obviously only shows the one PC (beth-pc)
 
[SIZE=2]Status for domain WORKGROUP on transport \Device\NetBT_Tcpip_{632388F7-47ED-409A
-941F-427972A4899C}
Browsing is active on domain.
Master browser name is: BETH-PC
Master browser is running build 2600
1 backup servers retrieved from master BETH-PC
\\BETH-PC
There are 1 servers in domain WORKGROUP on transport \Device\NetBT_Tcpip_{63
2388F7-47ED-409A-941F-427972A4899C}
There are 1 domains in domain WORKGROUP on transport \Device\NetBT_Tcpip_{63
2388F7-47ED-409A-941F-427972A4899C}
 
 
**Then I stop the computer browser service and what happens is the PC ends up using the DMB (ie Ubuntu) which is in subnet 1 and then the browse list shows only the computers from subnet 1 (see below)**
 
C:\Program Files\Support Tools>browstat status
&#12288;
Status for domain WORKGROUP on transport \Device\NetBT_Tcpip_{632388F7-47ED-409A
-941F-427972A4899C}
Browsing is active on domain.
Master name cannot be determined from GetAdapterStatus. Using \\UBUNTU
Unable to determine build of browser master: 2
\\\\UBUNTU . Version:04.09 Flags: 809a03 NT SERVER
1 backup servers retrieved from master UBUNTU
\\UBUNTU
There are 4 servers in domain WORKGROUP on transport \Device\NetBT_Tcpip_{63
2388F7-47ED-409A-941F-427972A4899C}
There are 1 domains in domain WORKGROUP on transport \Device\NetBT_Tcpip_{63
2388F7-47ED-409A-941F-427972A4899C}
 
 
I am pulling my hair out..Can it be that no LMB <---->DMB browse list sync occurs when using the 'WORKGROUP' model and not the domain model??  
 
 
[/SIZE]

---

