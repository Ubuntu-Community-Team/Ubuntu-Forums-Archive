---
title: "Can only access port 21 from WAN (yes I have port forwarding setup correctly)"
date: 2010-03-29
forum: General Help
---

### Post by brianjohn on 2010-03-29
Hi,
For some reason I can only access FTP on my Ubuntu machine in my house.  I have a number of apps running on it including FTP (port 21), mt-daapd (port 3689) and Confluence (port 8080).  I have these ports forwarded in my router configuration and have verified that they are open with this service: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/).  For some reason I can only access FTP from the WAN.  I can access everything from the LAN.  I have tried for hours but can't figure this out.

I tried adding 'Listen 8080' to my ports.conf file but then apache spit out this message:
$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs

I'm not even sure if the web apps I'm using are using apache or not, but I'm not sure how to tell for sure.

Can someone please help me get this working?

---

### Post by gmargo on 2010-03-29
So the ports are open on the router, and the router is configured to forward them.  Are the ports open on the Ubuntu box?  Is firewall software blocking them?  Are the services listening on all interfaces and not just localhost?

Here's how to find out who's using port 8080: "sudo lsof -i :8080"

---

### Post by Monotoko on 2010-03-29
Have you looked at the <Directory> </Directory> sections of your httpd.conf file?

By default i believe its set to "Deny To All"..if so set it to allow and see if that works.

---

### Post by brianjohn on 2010-03-29
> **gmargo said:**
> So the ports are open on the router, and the router is configured to forward them.  Are the ports open on the Ubuntu box?  Is firewall software blocking them?  Are the services listening on all interfaces and not just localhost?

Here's how to find out who's using port 8080: "sudo lsof -i :8080"

When I run that command I get the following (which I think is expected):
```
COMMAND  PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java    1104 confluence   28u  IPv6   6148      0t0  TCP *:http-alt (LISTEN)
```

Got this when I ran the same for port 3689:
```
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mt-daapd 23475 mt-daapd    9u  IPv4 281085      0t0  TCP *:daap (LISTEN)
```

To answer the rest of your questions I don't think there is any firewall software installed as Ubuntu Desktop is supposed to come with no firewall software installed and I haven't installed one.  Is there a way that I could double-check?

How can I tell what interfaces that the services are listening on?  I can connect from other computers on my LAN.

Sorry for all of the simple questions, I'm still relatively new to *nix.

Thanks for your help

---

### Post by brianjohn on 2010-03-29
> **Monotoko said:**
> Have you looked at the <Directory> </Directory> sections of your httpd.conf file?

By default i believe its set to "Deny To All"..if so set it to allow and see if that works.

When I open httpd.conf it is empty.  Is that normal?

Honestly I'm not even sure that the webapps I'm running are even using apache.

Thank you for your help

---

### Post by brianjohn on 2010-03-29
Regarding Firewall, I checked the status of ufw and it says it's inactive.  I don't know what other firewalls could be installed.

```
sudo ufw status
Status: inactive
```

---

### Post by Monotoko on 2010-03-29
> **brianjohn said:**
> When I open httpd.conf it is empty.  Is that normal?

Honestly I'm not even sure that the webapps I'm running are even using apache.

Thank you for your help

No worries.

Which web applications are you running? Did you get them from Synaptic?

It might be best to remove it and install apache2, as it usually "just works"

~Daniel

---

### Post by brianjohn on 2010-03-29
Here's another really strange piece of information - when I try to access these webapps using the WAN address from inside my LAN, it works and they load fine.

Thank you both very much for your help

---

### Post by brianjohn on 2010-03-29
> **Monotoko said:**
> No worries.

Which web applications are you running? Did you get them from Synaptic?

It might be best to remove it and install apache2, as it usually "just works"

~Daniel

I'm running confluence ([http://confluence.atlassian.com](http://confluence.atlassian.com)) and mt-daapd ([http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/)).  I downloaded confluence from Atlassian and I installed mt-daapd through apt-get.

---

### Post by Monotoko on 2010-03-29
> **brianjohn said:**
> Here's another really strange piece of information - when I try to access these webapps using the WAN address from inside my LAN, it works and they load fine.

Thank you both very much for your help

Based on this, i would say its probably a limitation of the router. You could confirm by installing a web package on another computer in the LAN and try to access it.

My router has the opposite problem, cant access it from the WAN address as it redirects me straight to the router login page.

---

### Post by brianjohn on 2010-03-29
> **Monotoko said:**
> Based on this, i would say its probably a limitation of the router. You could confirm by installing a web package on another computer in the LAN and try to access it.

My router has the opposite problem, cant access it from the WAN address as it redirects me straight to the router login page.

My router is running tomato (open source firmware) so I would think it could do this.  One thing I just thought of is that I've only checked from the WAN from work.  Is it possible that my work is blocking these ports outgoing?

---

### Post by gmargo on 2010-03-29
> **brianjohn said:**
> How can I tell what interfaces that the services are listening on?  I can connect from other computers on my LAN.

The output of lsof tells you, for instance the 8080 says "*:http-alt" - the asterisk (*) tells you it's listening on all interfaces.  It would say 127.0.01:http-alt (or perhaps localhost:http-alt?) if it was only listening  on the localhost interface.  There would be multiple lines if it was listening on, say, two out of three interfaces.  You can also tell from the output of "netstat -an | grep :8080", which will look similar.

---

### Post by gmargo on 2010-03-29
> **brianjohn said:**
> My router is running tomato (open source firmware) so I would think it could do this.  One thing I just thought of is that I've only checked from the WAN from work.  Is it possible that my work is blocking these ports outgoing?

I also run Tomato on my Linksys router.  It forwards http and ssh and bittorrent traffic just fine, and I can reference my external domain name internally as well.  However, I don't know about those other protocols.  Try setting up a dirt-simple web server on port 80?

You can probably test your work->home connection with telnet.  From work, "telnet home.address.xxx 21" should connect to the ftp server, and likewise for the other two ports.  If work is blocking the ports, I doubt you'd see a connect; it would probably just hang.

---

### Post by brianjohn on 2010-03-30
> **gmargo said:**
> I also run Tomato on my Linksys router.  It forwards http and ssh and bittorrent traffic just fine, and I can reference my external domain name internally as well.  However, I don't know about those other protocols.  Try setting up a dirt-simple web server on port 80?

You can probably test your work->home connection with telnet.  From work, "telnet home.address.xxx 21" should connect to the ftp server, and likewise for the other two ports.  If work is blocking the ports, I doubt you'd see a connect; it would probably just hang.

Well, I had a friend try from his house and the link worked, so I guess the problem is simply that my work is blocking some of these ports.  Strange.

Thank you both very much for your help.  Despite the fact that the issue as I stated it didn't exist, I was able to learn.

Thanks again!

---

