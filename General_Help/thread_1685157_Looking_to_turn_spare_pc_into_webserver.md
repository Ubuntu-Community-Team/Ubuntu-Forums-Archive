---
title: "Looking to turn spare pc into webserver"
date: 2011-02-10
forum: General Help
---

### Post by kr4zy1983 on 2011-02-10
Hello everyone I hope I am posting this in the right section if not please move it.

I have a spare duel core pc with 500GB HDD and 2GB memory so decided last night to do a full format and a complete install of ubuntu 10.10.

My mission is to turn it into a web server. I have installed xampp for Linux and everything seems to be running smooth.

I have ran into these problems and hope someone can help.
1) I used sudo apt-get install openssh-server and edited the sshd_config to change the port to 28. I have also opened the ports in my router but when i try to connect from another network pc i get connection refused.

2) I have a domain name I would like to assign to my server pc but don't know how to do it since "ifconfig" states 192.168.1.3 and my external IP from "whatsmyip.com" keeps changing.

Any help on these matters would be great.

Regards Kr4zy.

---

### Post by CrusaderAD on 2011-02-10
Install webmin. It makes configuring a web server WAY easier.

---

### Post by P4man on 2011-02-10
> **kr4zy1983 said:**
> 
1) I used sudo apt-get install openssh-server and edited the sshd_config to change the port to 28. I have also opened the ports in my router but when i try to connect from another network pc i get connection refused.

Did it work on the default port? Are you using the right syntax to connect to port 28

```
ssh user@pc -p 28
```
> 
2) I have a domain name I would like to assign to my server pc but don't know how to do it since "ifconfig" states 192.168.1.3 and my external IP from "whatsmyip.com" keeps changing.

You have a dynamic IP address from your provider. I recommend using no-ip to solve that. Sign up for a free account at [www.no-ip.org](www.no-ip.org). Create a DNS host redirect, something like yourname.no-ip.org. It will fill out your current IP address for you.

Now to keep it updated, install the client on your webserver

```
sudo apt-get install noip2
```

Follow directions, fill out all the info, and yourname.no-ip.org will always redirect your home LAN.

---

### Post by sffvba[e0rt on 2011-02-10
Oh wow... this thread is is so full of information I wanted to know... and I found it with out even searching :p

Thanks to all contributors and to OP for making it :guitar:


404

---

### Post by kr4zy1983 on 2011-02-10
God I love these forums so much!!!! 

Thank you CerealCypher & p4man.

All my problems are now solved and my server is now working with ssh and webmin on ubuntu 10.10.

No doubt if I come across any more issues ill be searching and then posting but can't believe I didn't install ubuntu earlier and get rid of windows ha ha!!!!!

Thanks again Kr4zy.

---

### Post by Dragonbite on 2011-02-10
Depending on your experience, there is also the Ubuntu Server based [[COLOR="Blue"]_Zentyal _[/COLOR]]("http://www.zentyal.org/")appliance or can install Zentyal (formerly eBox) on your own Ubuntu Server (as mentioned [[COLOR="Blue"]_here_[/COLOR]]("http://doc.zentyal.org/en/installation.html")).

It provides a web interface to managing most aspects of a SMB server.

---

### Post by CrusaderAD on 2011-02-10
> **kr4zy1983 said:**
> God I love these forums so much!!!! 

Thank you CerealCypher & p4man.

All my problems are now solved and my server is now working with ssh and webmin on ubuntu 10.10.

No doubt if I come across any more issues ill be searching and then posting but can't believe I didn't install ubuntu earlier and get rid of windows ha ha!!!!!

Thanks again Kr4zy.

No problem, glad to see you got it working! With webmin, ssh enabled and even phpmyadmin... the possibilities are endless :)

---

### Post by kr4zy1983 on 2011-02-10
Tiny bit more help needed sorry lol. I assumed everything was working fine (which it is) but...

Have the problems below "my internal server IP after using ifconfig is" inet addr:192.168.1.3

If I try to access  [http://myusername.no-ip.org](http://myusername.no-ip.org) from this pc (the one my server is running on) I get my router login page and not the xampp login page like when I open [http://localhost](http://localhost) or [http://192.168.1.3](http://192.168.1.3)

If I try to access [http://myusername.no-ip.org](http://myusername.no-ip.org) from my main pc on the network (not the server) I also get to my login page to my router and not the xampp login page I was expecting as if went to [http://192.168.1.3](http://192.168.1.3)

So I just decided to ring my dad and ask him to go to [http://myusername.no-ip.org](http://myusername.no-ip.org) and the result he just got was google chrome could not find this page.

I can understand that in my network I will be getting the router configuration when going to my IP address and getting the results I am supposed to by going to the pc's internal IP address from network pc's but what I don't understand is that I am getting a page can not be found error from out of network pc's.

I was thinking this could be something to do with the router firewall/port forwarding settings but have checked and they are open for internal ip 192.168.1.3 (this server IP)

I don't know if i must also place in the external IP when adding a port to the "nat>port mapping" settings in my router but also came to the conclusion that if I needed to add the external port to that I would have to do that every time I restarted the router as the IP changes (hence why i need no-ip.com)

Please please please does anyone have a solution to this as I am baffled and will not sleep until the problem is solved lol.

Kind regards Kr4zy.

---

### Post by P4man on 2011-02-10
You have to forward the ports.
A bit of IPv4 101. you router has 2 IP addresses. One public, facing the internet, and one internal, facing your home network. All your PCs have local IP addresses (192.168.x.x) that are not routable over the internet, and not accessible outside your local network.

To see your local IP address, type

```
ifconfig
```

This can be made static (just configure a static IP address) or DHCP, which, if your router is any good, will keep assigning the same IP address to the same machine.

To find your router's public IP address, use this:
[http://www.whatismyip.com/](http://www.whatismyip.com/)

Thats a dynamic IP address given to your router by your ISP. It will change every day or x days.

Now, using no-ip, what you did is link your no-ip.org domain to the **public **IP address **of your router**. Since you want requests made to that address to be forwarded to your webserver (or SSH server or whatever server), you will have to configure your router to forward those ports to the (local) IP address of your webserver. 

I cant give you exact instructions as every router is different, but essentially you have to configure it so port 80 and port 28 are forwarded to the ip address of your webserver. Note, many ISP's block incoming ports below 1024, if that is the case, you will need to configre your webserver and ssh server on a higher port, like 8080 and 2222. To access your website, people will have to go to
[http://yourname.no-ip.org:8080/](http://yourname.no-ip.org:8080/)

Last remark; a quick and dirty way is setting your webserver in the DMZ. That means ALL incoming requests from the internet to your public IP will be forwarded to that machine (and bypass the routers firewall if you have that enabled).

---

