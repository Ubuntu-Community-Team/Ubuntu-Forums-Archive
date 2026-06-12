---
title: "DNS entries vanishes after login"
date: 2006-02-22
forum: General Help
---

### Post by c_anindya on 2006-02-22
:cry: 
Hi,

My pc is connected to a switch(which is connected to a DSL modem) and gets IP from that. But, I want to keep two "fixed DNS server entry" in resolve.conf . But the problem is everytime I log in or do some system update thru aptget the DNS entries are gone since its taking the ip from switch. Could anybody help me in this regard?

thanks,
ani

---

### Post by nrwilk on 2006-02-22
Having the exact same problem.  I have to edit resolv.conf manually every day.  It takes out the first DNS entry and instead puts in the internal IP of my ethernet switch.

Also, I dunno if this is related, but I suspect that it is.  When installing Dapper, I get to the point where it checks to see if I have a DHCP protocol internet connection (which I do).  I select eth1 ( eth0 is an integrated port on my mainboard which never worked, eth1 is a cheap ethernet card which worked under Breezy and Hoary. ) and it claims that I do not have a DHCP connection.  I entered my info manually, but when Breezy has installed, it's always detected the connection in a couple seconds.  Is this a Dapper quirk, or is it my DHCP going insane?

---

### Post by dcstar on 2006-02-23
[QUOTE=c_anindya]:cry: 
Hi,

My pc is connected to a switch(which is connected to a DSL modem) and gets IP from that. But, I want to keep two "fixed DNS server entry" in resolve.conf . But the problem is everytime I log in or do some system update thru aptget the DNS entries are gone since its taking the ip from switch. Could anybody help me in this regard?

thanks,
ani[/QUOTE]
If you want to be really mean, just remove the write permissions from your resolv.conf file (after you have the correct info in it, of course.....)

---

### Post by lamego on 2006-02-23
Hello
I had a similar problme some time ago.
You will need to change the dhcp client configuration to not get the dns from DHCP .

sugo gedit /etc/dhcp3/dhclient.conf

Remove the domain-name  and domain-name-servers from the request option...

I think you will need to restart the dchp service...

---

### Post by nrwilk on 2006-02-23
[QUOTE=lamego]Hello
I had a similar problme some time ago.
You will need to change the dhcp client configuration to not get the dns from DHCP .

sugo gedit /etc/dhcp3/dhclient.conf

Remove the domain-name  and domain-name-servers from the request option...

I think you will need to restart the dchp service...[/QUOTE]

I'll try that today.

As for my Dapper problem, I was being much too hasty and not giving the Kubuntu devs enough credit.  They've actually made it so the the Dapper installer detects the two ethernet cards the other way around (the integrated port is now detected as eth1, and the add-on card is eth0).  Yay! :o 

I had just been selecting eth1 without looking at their names. DOH! :mad:

---

### Post by c_anindya on 2006-02-26
Hi,

Able to solve it finally, \\:D/ what I did? I modified, dhclient ofcourse.
did a sudo gedit /etc/dhcp3/dhclient.conf 
In the file after the section where it takes everything from switch, I 
added a line, prepend name-server "name server list"
this is working so far :cool:

---

