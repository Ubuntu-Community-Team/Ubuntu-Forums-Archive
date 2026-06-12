---
title: "Server IP Address Question"
date: 2010-08-06
forum: General Help
---

### Post by frozenfire0808 on 2010-08-06
I'm trying to play my Playstation 3 game Age of Booty online but it won't connect and I waited for ten minutes.I tried that several times. Then i tried to make a private match with a friend and it said NAT error. So I looked up ports for age of booty and ended up on this website 
[http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/PS3_Age_of_Booty.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/PS3_Age_of_Booty.htm)      I get the TCP/UDP and the Starting and Ending Port but on the website it shows             192.168.1.blank so do I have to change mine to that even though mine by default says 10.0.0.blank ?  and what do i put in the blank spot? I can't save it with nothing there.

---

### Post by PeEllAvaj on 2010-08-06
Not exactly an Ubuntu question, :).

So from my understanding you are trying to connect with your PS3 to your friend's PS3 over the internet to play Age of Booty (fun game by the way)?  If that's correct, you will need to determine the IP of your PS3. I don't have a PS3, so you can either figure it out from within their interface, or with an ubuntu computer on the network, you could use nmap.

192.168.0.x is a set of standard IPs used by most home networks, but 192.168.1.x and 10.0.x.x are also valid home networks.  The tutorial you were reading assumes your network is 192.168.0.x, so you will need to change that (and the IP itself) to whatever is the IP of your PS3.

Have I understood the problem, does this help you move forward at all?

---

### Post by frozenfire0808 on 2010-08-06
my PS3 has the following IP Adress 10.0.0.2  Subnet Mask 255.255.255.0  Default Router 10.0.0.1   Primary DNS 10.0.0.1 Secondary DNS 0.0.0.0   and  will changeing everything to the 192.168.1.??? make my ubunto internet not work?

---

### Post by PeEllAvaj on 2010-08-06
In your router's port forwarding, you should put 10.0.0.2 everywhere where your tutorial tells you to use 192.168.0.x.  This shouldn't affect any other computers on your network.

---

### Post by frozenfire0808 on 2010-08-06
ok i'll try that

---

### Post by frozenfire0808 on 2010-08-06
that worked excpt port 3658 it said  The specified port(s) are being used by other configurations. Please check your configurations of Remote Management, Port forwarding, Port Triggering, UPnP Port Mapping table, RIP, and Internet connection type       uhh i dont  know what to do

---

### Post by frozenfire0808 on 2010-08-06
since this is no longer a server IP address Question I'll start a new thread tommrow with a title of  How to open port 3658?    thanks everyone who helped or at least looked to see if they could help

---

