---
title: "decline dhcp offer?"
date: 2012-01-06
forum: General Help
---

### Post by hg088 on 2012-01-06
is there a way to configure dhclient or something to reject/decline an specific ip address?

---

### Post by 2F4U on 2012-01-06
You could block tcp/udp requests for that particular ip address through a firewall.

---

### Post by hg088 on 2012-01-06
a few years back when i was using windows i remember i could block traffic to an specific ip, but i didnt see any option to identify or block DHCPREQUEST packets.

can u point me a firewall that can do this?

thanks for the reply by the way :)

---

### Post by 2F4U on 2012-01-06
This should block communication for a specific IP address

```
sudo ufw deny from 188.162.67.197
```

UFW (Uncomplicated FireWall) is the default firewall that comes with Ubuntu
However, when you add a rule it gets appended. So if you had a rule before that  allows everyone to connect to your machine, it also allows the  IP you’re trying to block, to connect to your machine.

---

### Post by dandnsmith on 2012-01-06
I'm not sure why you'd be concerned about being allocated a particular IP address (which is what the question asks). I don't believe the dhcp client has such a mechanism - after all you're asking for an address which should be used to operate on the internet.
AFICT that rule will block incoming from a particular IP address - but that wasn't the stated aim.

Do we need the request, and the reason for asking it spelled out, so that a 'proper' answer can be vouchsafed?

---

### Post by hg088 on 2012-01-06
thanks for the info [2F4U]("http://ubuntuforums.org/member.php?u=1357554") i didnt know that

the reason im trying to get dhclient to reject an ip is because when i do an ip release and a renew the dhcp servers always offers the same ip

i know that this is probably because of my mac, but in windows xp im able to get a diferent ip without changing my mac

---

### Post by lykwydchykyn on 2012-01-06
DHCP servers generally remember past leases and try to consistently give the same IP to the same MAC address every time.

So the simple solution here is to make your machine spoof a different MAC address.  Then it should get a different IP.

See here:

[http://linuxhelp.blogspot.com/2005/09/how-to-change-mac-address-of-your.html](http://linuxhelp.blogspot.com/2005/09/how-to-change-mac-address-of-your.html)

---

### Post by bab1 on 2012-01-06
> **hg088 said:**
> thanks for the info [2F4U]("http://ubuntuforums.org/member.php?u=1357554") i didnt know that

the reason im trying to get dhclient to reject an ip is because when i do an ip release and a renew the dhcp servers always offers the same ip

i know that this is probably because of my mac, but in windows xp im able to get a diferent ip without changing my mac

Does [**_[COLOR="Blue"]this[/COLOR]_**]("http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/") help?

---

### Post by hg088 on 2012-01-06
thanks [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141") im definitely gonna try that

though is weird that i can do this in xp without changing the mac

---

### Post by bab1 on 2012-01-06
> **hg088 said:**
> thanks [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141") im definitely gonna try that

though is weird that i can do this in xp without changing the mac

You don't need to change (spoof) the MAC.  You just need to release the current lease.

---

### Post by hg088 on 2012-01-06
i know that most people can do just: sudo dhclient -r && sudo dhclient eth0

but thats not working for me

---

### Post by dcstar on 2012-01-07
> **hg088 said:**
> i know that most people can do just: sudo dhclient -r && sudo dhclient eth0

but thats not working for me

Try deleting the contents of the /var/lib/dhcp3/ folder before restarting the dhclient.

---

### Post by hg088 on 2012-01-07
i made a bash script that allows me to get a new public ip from my isp's dhcp server
```
sudo dhclient -r -v eth2 && sudo rm /var/lib/dhcp/* 
sleep 1
sudo sh -c "echo 'interface \"eth2\" { send dhcp-requested-address 1.2.3.4;}' >> /etc/dhcp/dhclient.conf" 
sleep 1 
sudo dhclient -v eth2 & sleep 1 sudo sed -i '$ d' /etc/dhcp/dhclient.conf 
sleep 3 
sudo killall dhclient 
sleep 6 
sudo dhclient -v eth2
```

---

