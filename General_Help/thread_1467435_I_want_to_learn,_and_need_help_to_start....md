---
title: "I want to learn, and need help to start..."
date: 2010-04-30
forum: General Help
---

### Post by SalinasIT on 2010-04-30
Hi,
 
i had alot experience on windows based servers, and now i want to learn about linux, i want some advice on how to start properly.
 
First i want to understand how can i design a Basic Linux Solution similar to Windows based Servers.
 
Example:
Using Windows 2003 Server STD as OS i ussually start with a basic infraestructure using 4 Virtual Servers (fisical servers or virtual servers depending the budget)
 
1st server.- Configured as Primary Domain Controller (AD, DNS, DHCP)
2nd server.- Configured as Exchange Server for mailing and colaboration.
3rd server.- Configured as a Terminal Server, and File Sharing.
4th server.- Configured as Firewall and Proxy using ISA
 
I want to know how would be a Linux design similar to my example.
 
I just want to clarify my concepts before start my learning and reserch...
 
Sorry for my poor english.
 
Thanks

---

### Post by The Real Dave on 2010-04-30
Perhaps the [Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") could help?

Filesharing can be done with Samba, Proxy and Firewall with Squid and IPtables.

I've no experience with the rest tbh. You can always run W2k3 in a VM on Ubuntu if needed :)

---

### Post by SalinasIT on 2010-04-30
> **The Real Dave said:**
> Perhaps the [Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") could help?
 
Filesharing can be done with Samba, Proxy and Firewall with Squid and IPtables.
 
I've no experience with the rest tbh. You can always run W2k3 in a VM on Ubuntu if needed :)
 
Thanks
 
im starting to read a lot of guides, and i want to clarify my mind setting some goals, im gonna take a look on Samba, squid and IPtables.
 
My big problem it's about how can i distribute all on my solution, for example with microsoft i know how many servers i need, and wat can i put alone or mixed.
 
But on Linux im totally lost, some one said to me that i can put all togeter with a powerfull machine. (I don't know if that would be a god practice)
 
My first goal it's to understand how can i design my server infraestructure using Linux, and with that, start to read about it.
 
Im reading Ubuntu Pocket Guide, and i hope that help me to leave my Microsoft way of think :p

---

### Post by The Real Dave on 2010-05-01
> **SalinasIT said:**
> Thanks
 
im starting to read a lot of guides, and i want to clarify my mind setting some goals, im gonna take a look on Samba, squid and IPtables.
 
My big problem it's about how can i distribute all on my solution, for example with microsoft i know how many servers i need, and wat can i put alone or mixed.
 
But on Linux im totally lost, some one said to me that i can put all togeter with a powerfull machine. (I don't know if that would be a god practice)
 
My first goal it's to understand how can i design my server infraestructure using Linux, and with that, start to read about it.
 
Im reading Ubuntu Pocket Guide, and i hope that help me to leave my Microsoft way of think :p

I know that many people will use VMs within Ubuntu, even VMs of other Ubuntu Servers, if only for simplicity. One rouge process won't take down the whole server for example, and it's easier to perform upgrades, backups etc. Security is probably improved.

That said, I've never VMd on my Ubuntu Server, but mine is just a simple home server with Squid and a few other things. Squid is absolutely terrific, and I'd recommend Squint if you wish to monitor bandwidth usage :)

---

### Post by SalinasIT on 2010-05-01
> **The Real Dave said:**
>  
That said, I've never VMd on my Ubuntu Server, but mine is just a simple home server with Squid and a few other things. Squid is absolutely terrific, and I'd recommend Squint if you wish to monitor bandwidth usage :)
 
Im going to check that tomorrow, bandwith usage is always important ;)
 
I think Domain controller and Proxy-Firewall it going to be the easiest part, but i don't have a clue about someting like Terminal Server and Exchange Server.
 
But im just starting with linux :D

---

