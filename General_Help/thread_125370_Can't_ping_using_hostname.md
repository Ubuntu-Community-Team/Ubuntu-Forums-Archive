---
title: "Can't ping using hostname"
date: 2006-02-03
forum: General Help
---

### Post by TC10284 on 2006-02-03
Hey all,

I apologize if I ask a n00b question.
I am trying to setup about about 6 older Pentium II systems with Ubuntu 5.10 to be used with BOINC distributed computing program. I use BOINCView to monitor the Windows systems that are currently already running BOINC. I applied a hostname to the Ubuntu machines such as Ubuntu-1, Ubuntu-2, etc. (1-8). 
I am using the BrazilFW 2.26 router OS as my DHCP server and two Win Server 2003 systems that are domain controllers/DNS servers that are replicated as the DNS servers. 
My problems is that I cannot ping the Ubuntu machines using their hostname (Ubuntu-1, etc). I would like to be able to do this as I setup BOINCView to get the status of the machines over the network. 
I have tried switching the DHCP server to Win Server 2003 and it would show the currently leased IP address of the Ubuntu machine but not it's hostname and I still could not ping the Linux machines using the hostname of the machine. I am not sure what I am doing wrong or not doing. Is it just one of those Windows to Linux things? Do I need to setup an LDAP/Kerberos or DNS server on Ubuntu?

Thanks for any help guys

---

### Post by dcstar on 2006-02-03
[QUOTE=TC10284]Hey all,

I apologize if I ask a n00b question.
I am trying to setup about about 6 older Pentium II systems with Ubuntu 5.10 to be used with BOINC distributed computing program. I use BOINCView to monitor the Windows systems that are currently already running BOINC. I applied a hostname to the Ubuntu machines such as Ubuntu-1, Ubuntu-2, etc. (1-8). 
I am using the BrazilFW 2.26 router OS as my DHCP server and two Win Server 2003 systems that are domain controllers/DNS servers that are replicated as the DNS servers. 
My problems is that I cannot ping the Ubuntu machines using their hostname (Ubuntu-1, etc). I would like to be able to do this as I setup BOINCView to get the status of the machines over the network. 
I have tried switching the DHCP server to Win Server 2003 and it would show the currently leased IP address of the Ubuntu machine but not it's hostname and I still could not ping the Linux machines using the hostname of the machine. I am not sure what I am doing wrong or not doing. Is it just one of those Windows to Linux things? Do I need to setup an LDAP/Kerberos or DNS server on Ubuntu?

Thanks for any help guys[/QUOTE]
Just manually add the Ubuntu machines into the "hosts" file of the Windows machine(s).

---

### Post by TC10284 on 2006-02-03
Thanks for your reply.

To be honest though, I'd rather set a group of static IPs instead than worry with doing that that. True, I could add them on the machine that is running BOINCView but I'd like to have it to work on each system properly.
Is there another way to solve this issue?

---

### Post by dcstar on 2006-02-03
[QUOTE=TC10284]Thanks for your reply.

To be honest though, I'd rather set a group of static IPs instead than worry with doing that that. True, I could add them on the machine that is running BOINCView but I'd like to have it to work on each system properly.
Is there another way to solve this issue?[/QUOTE]
You have a DHCP server assign the names when it gives out a DHCP address, and the DHCP server is tied to your DNS server (somehow).

Either way something has to match up the IP addresses to the names, it won't happen by itself.

---

### Post by TC10284 on 2006-02-04
I thought that giving the system a hostname would allow the hostname to be sent to the DHCP server when an IP was leased to the system which would then register it with a DNS server. 
Would setting up a DNS server in Linux get around having to give all systems static IP's and/or putting the names of 5+ Ubuntu systems in a Windows hostfile?
I don't mean to sound lazy or "unthankful" for your replies, I just figure that there's got to be a more flexible way so to speak.

---

### Post by dcstar on 2006-02-04
[QUOTE=TC10284]I thought that giving the system a hostname would allow the hostname to be sent to the DHCP server when an IP was leased to the system which would then register it with a DNS server. 
Would setting up a DNS server in Linux get around having to give all systems static IP's and/or putting the names of 5+ Ubuntu systems in a Windows hostfile?
I don't mean to sound lazy or "unthankful" for your replies, I just figure that there's got to be a more flexible way so to speak.[/QUOTE]
A DHCP server *sends* IP addresses to it's clients (and it can assign a Hostname as well), clients don't send Hostname info to DHCP servers. Some DHCP servers can update a DNS server with info it sends out, (don't know how this is done in Linux, done it in Windows myself).

You can set up a DNS server with all the Static IPs and Hostnames entered, that would solve your problem.

The point is that the data has to be entered somewhere, a DNS server just makes it a single point of entry that other systems have access to - but setting up a DNS server has its own overheads, so you have to decide it if is easier just to have  Hosts file data that you can copy between your PCs - both ways will probably work fine in normal use.

---

