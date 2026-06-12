---
title: "I am trying to connect to a Network"
date: 2011-10-12
forum: General Help
---

### Post by Gladian00b on 2011-10-12
I am trying to connect an old Pentium III running Lubuntu to my school's network through the wired network ethernet protocol with automatic settings, but it isn't connecting!  This year, the school got new Windows 7 computers, and the section of the school I am working in had to be rewired due to remodeling.  If it has anything to do with the DHCP Client ID, I don't understand much of it at all.  MAC Address filtering could also be a problem.

If it is a DHCP problem, I would need to have access to DHCP Client ID generators that make available IDs.  Again, I don't understand DHCP very much.  All I know about it is that it can be used for PXE.  I have no access to the router, so I can't add exceptions to the filter list for MAC Addresses.  I do need help, however.  I have access to other computers, so I can still use the Internet.

The question would be this:  Am I blocked because of MAC Address filters, or lack of DHCP Client IDs?

---

### Post by cryptotheslow on 2011-10-12
> **Gladian00b said:**
> 
The question would be this:  Am I blocked because of MAC Address filters, or lack of DHCP Client IDs?

There's a whole raft of ways to prevent "unknown" devices using a network. Only your network administrator would be able to tell you definitively one way or another what is in place.

---

### Post by Gladian00b on 2011-10-14
OK, but I am assuming this is linked to the new Windows 7 computers.  The students are logging into the domain, unlike last year, which they used Novell client services.

---

### Post by SteveDee on 2011-10-16
> **Gladian00b said:**
> 

The question would be this:  Am I blocked because of MAC Address filters, or lack of DHCP Client IDs?

I doubt that your school is using MAC filtering, as they would have to maintain a list of all school hardware and keep updating it as old computers were chucked out and new ones bought in. Its more likely that the school has a domain, and you are not part of it. But you don't say if you were able to connect last year (before the changes).

So, from the little information you have supplied, here are a couple of possibly useless suggestions.

The first basic check is to try to ping another networked machine.
Open a terminal (from menu Accessories > LXTerminal) and type:-
```

ping {ip address}

```
...where {ip address} is the ip of a known computer/server on the network.

As your network probably supports internet connection, you could also ping a website like this:-
```

ping www.bbc.co.uk

```
If these tests work it shows you have basic network connectivity.

It sounds like your school has a network domain, so you wont be able to use resources without joining the domain. But here is an easy test which only requires you to know the domain name, the name of a network server or your network Windows 7 desktop machine, and your usename and password;

Start the Synaptic Package Manager and search for "rdesktop". Install this package.

Now open a terminal and type:-
```

rdesktop -d {domain name} -u {your username} {known computer name}

```

Here are a couple of examples:-
```

rdesktop -d myschool -u tony 192.168.0.15

rdesktop -d Hogwarts -u harry room7-pc02


```

NOTE: Be aware that if you do this using a Win7 desktop name/ip it will bump off the currently logged in user on that machine (so only use your own machine...not the headmaster's). But if you do this specifying a server name, it will just create a new desktop session.

What you should see (if this works) is a blue Win7 login screen (with your name on it) on your Lubuntu computer!

Does any of this rubbish help?

---

### Post by Gladian00b on 2011-10-26
It doesn't even let me ping.  The terminal said there is no network connection, and yet the light on my hub works just fine.  It looks like it has a lot to do with the network protocols.  I will ask my network administrator.  

Also, there is no access to the Internet or any of the other network resources.  I can't get the requested packages without an internet connection through the Lubuntu computer.

---

### Post by Weirdy on 2011-10-26
For fear of being too obvious - plug in and run ifconfig - do you get an IP address? Win 7 domains etc etc won't stop you getting an IP.

---

### Post by SteveDee on 2011-10-26
> **Gladian00b said:**
> It doesn't even let me ping...

Are you able to ping from one networked MS Windows machine to another?
I ask this because the ping port may be blocked on your network by firewall or other security settings.

---

### Post by Gladian00b on 2011-10-28
No, the pings aren't working with the windows 7 computers either.
```

Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\me>ping google.com

Pinging google.com [74.125.224.113] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 74.125.224.113:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

C:\Users\me>ping bbc.co.uk

Pinging bbc.co.uk [212.58.241.131] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 212.58.241.131:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

```I can still ping the school router, with a 100% success.  I find it strange that it knows what the IP addresses for these sites are, but that's probably the dns.

---

### Post by tonysathre on 2011-10-28
Have you tried a DHCP request?
```

sudo dhclient
```

If you can't ping out it's possible that ICMP is being filtered at the gateway but I don't see why. I assume your school actually has an active internet connection because DNS seems to be resolving. Can you browse those websites that you tried to ping?

Post an ipconfig /all from one of the Windows boxes.
Tony

---

### Post by Gladian00b on 2011-10-28
Yes, I have been able to access the sites that I pinged.  I am not at the Lubuntu computer at the moment, but I will try a dhcp request.

---

### Post by SteveDee on 2011-10-28
> **Gladian00b said:**
> No, the pings aren't working with the windows 7 computers either....

...the firewall is probably blocking ICMP.

You didn't say if you can ping the router from Win7 or Lubuntu (or both).

Also do as Weirdy suggested or (right-click on the network icon in the desktop panel) to see Connection Information. This should show if the Lubuntu machine has been assigned a suitable IP address (i.e. an ip in the same range as the network).

---

### Post by Gladian00b on 2011-10-28
As for the Boxes of Windows, yes, I did an ipconfig all, and there appears to be a 6-to-4 and isatap tunnel adapters listed.  All I know is that these are tunnel adapters, but I have no idea how they function.

---

### Post by Gladian00b on 2011-10-28
I pinged from a Windows 7 computer

---

### Post by Gladian00b on 2011-11-01
> **tonysathre said:**
> Have you tried a DHCP request?
```

sudo dhclient
```

I tried this (after having received your suggestion), it went through all the intervals, but it didn't work.  The problem *probably* isn't DHCP related, but thanks for your help.

---

