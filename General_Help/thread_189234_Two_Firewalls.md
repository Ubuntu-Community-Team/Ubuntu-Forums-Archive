---
title: "Two Firewalls"
date: 2006-06-04
forum: General Help
---

### Post by hanzomon4 on 2006-06-04
I setup a custom iptables script, but it has no effect...

When I run a port scan all ports show up as blocked except icmp, if I flush my firewall and preform the same test I get the same results.

So have I missed something :confused:

---

### Post by nanotube on 2006-06-05
so... why is your subject called "two firewalls" ? :)
but anyway, i am not sure what you are trying to accomplish, but for an example of a simple but robust iptables setup, go to the first link in my sig, and find the firewall section. it has a nice iptables setup.

---

### Post by hanzomon4 on 2006-06-05
[QUOTE=nanotube]so... why is your subject called "two firewalls" ? :)
but anyway, i am not sure what you are trying to accomplish, but for an example of a simple but robust iptables setup, go to the first link in my sig, and find the firewall section. it has a nice iptables setup.[/QUOTE]

I say two firewalls because when I stop  my custom firewall my ports remain blocked as if a firewall is still running

This is the guide that Iam using [iptables]("http://doc.gwos.org/index.php/IptablesFirewall")

---

### Post by ticool on 2006-06-05
Nearly all standard service are bound to localhost... which ports do you expect to see?

Are you sure your services are bound to the right device?
Are you behind a router("NAT-Firewall")? How do you scan your Ports and from where are doing it?

---

### Post by hanzomon4 on 2006-06-05
[QUOTE=ticool]Nearly all standard service are bound to localhost... which ports do you expect to see?

Are you sure your services are bound to the right device?
Are you behind a router("NAT-Firewall")? How do you scan your Ports and from where are doing it?[/QUOTE]
I expect for all of the ports that are scaned to show up as blocked, and they all do except icmp, but what confuses me is, if I stop the firewall the test still show the same results that it shows when I have the firewall running

Iam not sure what a local host is and if my services are bound to the right device

My dsl modem acts as a router, its a BellSouth FastAccess B90-220030-04 westell

I used these to websites to test my firewall [sygate]("http://scan.sygatetech.com/")
[grc]("https://grc.com/x/ne.dll?bh0bkyd2")

And here is my script if that will help

> #!/bin/bash 

# No spoofing 
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ] 
then 
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter 
do 
echo 1 > $filtre 
done 
fi 

# No icmp 
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all 
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts 

#load some modules you may need 
modprobe ip_tables 
modprobe ip_nat_ftp 
modprobe ip_nat_irc 
modprobe iptable_filter 
modprobe iptable_nat 

# Remove all rules and chains 
iptables -F 
iptables -X 

# first set the default behaviour => accept connections 
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script 
iptables -N FIREWALL 
iptables -N TRUSTED

#Allow ESTABLISHED and RELATED incoming connection 
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Send all package to the TRUSTED chain 
iptables -A FIREWALL -j TRUSTED 
# DROP all other packets 
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain 
iptables -A INPUT -j FIREWALL 
# DROP all forward packets, we don't share internet #connection in this example 
iptables -A FORWARD -j DROP 

# Allow https 
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT 


# End message 
echo " [End iptables rules setting]"


---

### Post by ticool on 2006-06-05
Normaly your DSL-Router should be a NAT-Router! This means the router don't knows to which PC he has to forward the incoming packets if the computer itself didn't send another package right before that. When you browse to ubuntu.org the router knows that your pc is waiting for the answer from ubuntu.org and redirects the packets to your PC. If there was no former request of your PC the Router just drop the packets... so in your case when you just externaly scan some ports...
They will be dropped, and your scanner expects them to be closed.
You can forward the Ports in your Router-config than they will be forwarded to your PC so you can externaly reach your PC... But you don't have any reasons for that else you run a apache or something like that...

And remember Port are closed if they aren't bound to a service...

---

### Post by hanzomon4 on 2006-06-05
[QUOTE=ticool]Normaly your DSL-Router should be a NAT-Router! This means the router don't knows to which PC he has to forward the incoming packets if the computer itself didn't send another package right before that. When you browse to ubuntu.org the router knows that your pc is waiting for the answer from ubuntu.org and redirects the packets to your PC. If there was no former request of your PC the Router just drop the packets... so in your case when you just externaly scan some ports...
They will be dropped, and your scanner expects them to be closed.
You can forward the Ports in your Router-config than they will be forwarded to your PC so you can externaly reach your PC... But you don't have any reasons for that else you run a apache or something like that...

And remember Port are closed if they aren't bound to a service...[/QUOTE]

Okay I kinda get what your're saying, the scanner is basically scanning my router and since I don't have any services like bittorent the ports show up as blocked because nothing is using them

---

### Post by thasheep on 2006-06-05
[QUOTE=hanzomon4]I expect for all of the ports that are scaned to show up as blocked, and they all do except icmp, but what confuses me is, if I stop the firewall the test still show the same results that it shows when I have the firewall running

Iam not sure what a local host is and if my services are bound to the right device

My dsl modem acts as a router, its a BellSouth FastAccess B90-220030-04 westell

I used these to websites to test my firewall [sygate]("http://scan.sygatetech.com/")
[grc]("https://grc.com/x/ne.dll?bh0bkyd2")

And here is my script if that will help[/QUOTE]
Your script accepts everything. I'll edit this post to explain why.

(edit)Sorry, I was wrong :p
But, you could replace the iptables comands with the following to achieve the same.
```
#!/bin/bash
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts 

## iptables firewall
iptables -F
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Allow https
iptables -A INPUT -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT
```

---

### Post by hanzomon4 on 2006-06-05
I found this strange problem with both my script and yours; it makes everything slow, like 5 min after login to get the desktop loaded.

I read around and saw that if your network config did not have auto lo (loopback) you could end up with this problem, so I put this in  my firewall script to see if it would fix problem
```
iptables -A INPUT -i lo -j ACCEPT 
iptables -A OUTPUT -o lo -j ACCEPT
```
It didn't work.

I stopped the fire wall with 
```
sudo /etc/init.d/firewall stop
```
and  every thing went back to normal.

Any idea what could be wrong with both scripts that would cause this problem?

---

