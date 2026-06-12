---
title: "Shared Network Drives and Printers Problem"
date: 2010-02-06
forum: General Help
---

### Post by chperry on 2010-02-06
I have a small network at home with 3 XP machines and two Ubuntu machines (one of the Ubuntu machines dual boots XP).  I have two of the XP machines have external hard drives that are shared and can be seen by the other XP machines.  One of the XP machines has a printer that can be seen by the other XP machines.  Neither Ubuntu machine can see the drive share or the printer share.  The XP machines have McAfee installed and I have checked the firewall settings to make sure all of the machines are "trusted".  All machines are part of the same workgroup.  What am I doing wrong?  When I try to browse for a samba printer, none are found.  When I try to add a network drive, it sees the Windows network, but none of the machines.  Is there some firewall magic I need to do?

---

### Post by chperry on 2010-02-06
More info.
nmap gives the following for the XP machine containing both a shared drive and a shared printer (neither of which I can "see" in Ubuntu)

Port     State  Service
135/tcp  open   msrpc
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
515/tcp  open   printer
2869/tcp open   unknown
6646/tcp open   unknown

Hope this helps.

---

### Post by chperry on 2010-02-09
Bump.

---

### Post by gordintoronto on 2010-02-10
Here's what I do: open Nautilus, select "network," double-click on "Windows Network," double-click on the workgroup, double-click on a computer, double-click on a share.  How far can you get when you try that?

---

### Post by chperry on 2010-02-12
When I double click Windows Network I get a blank window.  None of my Windows computers are shown, even though 2 of them have shares.

---

### Post by Morbius1 on 2010-02-12
From one of your Linux machines, post the output of the following commands:

Open **Terminal**
Type **smbtree**
Type **findsmb**

It should give you a status of how your linux machine sees the network. If we're lucky it will also output error messages which will help in the diagnostics of the problem.

---

### Post by chperry on 2010-02-12
smbtree gives:

cli_start_connection: failed to connect to 192.168.1.1<20> (192.168.1.1). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to WRT610N<20> (192.168.1.1). Error NT_STATUS_CONNECTION_REFUSED

findsmb gives:

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     WRT610N       +[	WORKGROUP     ]

the wrt610n is my router.

Thanks

Charles

---

### Post by Morbius1 on 2010-02-13
I've never seen a router show up in the output of smbtree of findsmb. Not only that but it appears your router has a workgroup name. 

It would be interesting to see what would happen if you ( temporarily ) disable not only the windows and linux firewalls ( if you configured a linux firewall ) but also the anti-virus software on windows and see if it works. Anti-Viurs software on windows has become very sophisticated lately and it might have an impact on accessing shares.

Can you access the Windows box by ip address in Nautilus: **smb://192.168.0.100** [COLOR=Blue]*( change 192.168.0.100 to match the ip address of the windows box )*[/COLOR]

I don't know if you're aware of this but your router allows something called "**DHCP Reservation**". It allows all your boxes to get their IP addresses from the router using DHCP as normal but the router will assign the exact same IP address to the exact same box everytime that box enters the network. One way to utilize that feature is to access each box by IP Address and then "Bookmark" it ( from Nautilus, select **Bookmarks > Add Bookmark** ). It will then show up under Places in Nautilus just like a "mapped drive" does in Windows.

---

### Post by chperry on 2010-02-13
That worked.  I could see the computer in question and browse the drives.  I was able to set a bookmark to the shared drive.  

I was able to map the printer by adding a windows printer via smb and entering the address: smb://192.168.1.xxx/$print and following the steps to install the driver. 

I am using DHCP Reservation for the machines that have shares. 

It is very odd that my router appears to be blocking me "seeing" the other machines.

Thanks

Charles

---

### Post by ceros on 2010-03-08
You could also try changing the workgroup name for your router. I have an WRT610N router as well and it's using an old version of Samba (3.0.25c). I'm guessing there are problems with using two completely different versions of Samba in the same workgroup.

---

