---
title: "reverse proxy"
date: 2012-04-25
forum: General Help
---

### Post by slaz on 2012-04-25
Hi,

I have setup a proxy server running squid and dansguardian on ubuntu server 11.10. Everything is running except the reverse proxy part. I made a shell script in /etc/init.d/

iptables -A INPUT -i eth1 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 8080 -j ACCEPT
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080 

this doesn't seem to be working correctly, when I connect a computer to the lan it should be automaically proxied. I have to manually set the proxy in the browser, defeating the purpose of this server.

I also want some IP addresses to be allowed out on port 80 using the following command but doesn't work either.
iptables -t nat -I PREROUTING -m tcp -p tcp -s 192.168.0.5 --dport 80 -j ACCEPT

I don't fully understand iptables, so any help is appreciated.

Thanks,
slaz

---

### Post by SeijiSensei on 2012-04-25
The directive should read "to-ports" rather than "to-port".  Run the command "man iptables" for details.

The other PREROUTING command looks correct to me.  I have the identical configuration on a gateway I manage for a client.  

I suggest you check your ruleset and make sure the REDIRECT actually does follow the other PREROUTING commands.  (I know you used -I for those, but it always helps to check.)  Use the command "iptables -t nat -L -nv" to list the NAT table.  If you leave out the "-t nat" it will list the FILTER table by default.

You don't really need the INPUT rules unless you have a default policy of DROP set for that chain. You'll see the policies in place if you use the command I just gave you without the "-t nat" option.

---

