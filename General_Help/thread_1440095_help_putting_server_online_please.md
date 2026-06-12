---
title: "help putting server online please"
date: 2010-03-27
forum: General Help
---

### Post by jmr423 on 2010-03-27
Hey, so I just finished setting up a Ubuntu server with lamp/proftpd/phpbb3/openssh and everything works 100% in my local network. My next goal is to be able to access my lamp server and proftpd through the internet. I am using a gigaset se567 router and my isp blocks ports 21.25.80.110.6667.135-139.443.445.1433.1434. I also have a dynamic external ip however my ubuntu servers internal ip is static. How do i connect to my server through the internet if they block http port 80 and ftp post 21? Another thing i was thinking of using is dyndns to link my dynamic ip to a domain name but i could not find any good guides for my situation. 

Can anyone help me put my web server and ftp access online and connect it to a domain name or at least direct me to a good guide?


Ports block by isp --- 21.25.80.110.6667.135-139.443.445.1433.1434

---

### Post by efflandt on 2010-03-27
Note that DNS cannot specify ports.  So once you get dynamic DNS to point your fully qualified domain name (FQDN) at your public IP, configure your servers for non-standard ports, and forward those non-standard ports on your router to server's private IP, you need to include the non-standard port in the URL like hostname.domain:8080 for an http URL or something else for ftp.

If you want to not require special ports in a URL, you would need to use a redirection service that could tack the necessary port onto a URL redirection.

---

### Post by jmr423 on 2010-03-27
> **efflandt said:**
> Note that DNS cannot specify ports.  So once you get dynamic DNS to point your fully qualified domain name (FQDN) at your public IP, configure your servers for non-standard ports, and forward those non-standard ports on your router to server's private IP, you need to include the non-standard port in the URL like hostname.domain:8080 for an http URL or something else for ftp.

If you want to not require special ports in a URL, you would need to use a redirection service that could tack the necessary port onto a URL redirection.

thanks for your reply, it helped me understand what i need to do but i kind of need some more help with doing these steps. So i im first going to work on getting the ports forwarded to 81 and then worrie about the dynamic ip address and dns after that. 

So i went into the  /etc/apache2/ports.conf and changed both the listen port and the virtualhost to 81 and the ssl port to 450. and then i tried accessing my site through my internal ip and i am able to access is through both port 80 and 81. (the ssl port 450 doesnt work but i do not care about that atm). i also change it from port 80 to 81 in /etc/apache2/sites-enabled/000-default  i restarted Apache. I then followed this guide 

[http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/Apache.htm](http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/Apache.htm)

to forward port 81 and port 450 and then went to my external ipaddress:81 and it does not connect.

What am i doing wrong?

---

### Post by 3rdalbum on 2010-03-27
> **jmr423 said:**
> 

to forward port 81 and port 450 and then went to my external ipaddress:81 and it does not connect.

What am i doing wrong?

Is the router forwarding to the correct internal IP address of your computer, and are you sure you're typing in the external IP address of the router when you're attempting to test it? The external IP address can be found by going to [www.whatismyip.com](www.whatismyip.com) from within your network.

---

### Post by jmr423 on 2010-03-27
> **3rdalbum said:**
> Is the router forwarding to the correct internal IP address of your computer, and are you sure you're typing in the external IP address of the router when you're attempting to test it? The external IP address can be found by going to [www.whatismyip.com]("http://www.whatismyip.com") from within your network.

I did this single step of this guide
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3)
> **7 Configure The Network**

  Because the Ubuntu installer has configured our system to get its  network settings via DHCP, we have to change that now because a server  should have a static IP address. Edit */etc/network/interfaces  * and adjust it to your needs (in this example setup I will use the  IP address *192.168.0.100*): 
 vi /etc/network/interfaces
                # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1          Then restart your network: 
 /etc/init.d/networking restart
I changed the address to 192.168.245.10 which i can conect to if im in my network. i then changed the gateway ip to the ip i use to connect to my router. I then went to my router and followed the other guide to redirect it to port 81 and put in 192.168.245.10 and i went to the site you are linking "[www.whatismyip.com]("http://www.whatismyip.com/")" and used the ip address that it showed. i typed in "157.55.45.78:81" (this is not my real ip address that [www.whatismyip.com]("http://www.whatismyip.com") showed) and it did not work.

---

### Post by junapp on 2010-03-27
Leave your server responding on port 80. No need to change that. Let the router listen on external port 81, and have it redirect to your server's lan ip, on port 80. What model of router do you have?

---

### Post by jmr423 on 2010-03-27
> **junapp said:**
> Leave your server responding on port 80. No need to change that. Let the router listen on external port 81, and have it redirect to your server's lan ip, on port 80. What model of router do you have?


i have a gigaset se567 router,

could i have made a mistake filling out the 

netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255 ?

i just copied it from the guide without changing it.


I changed the interfaces file to 

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth1 inet static
        address 192.168.254.10
        netmask 255.255.255.0
        gateway 192.168.254.254


I can now only connect to the local server through port 81

---

### Post by junapp on 2010-03-27
is your router set to have 192.168.254.254 as its address? Any reason in particular you chose that? Not that it matters all that much in this particular case I don't think. 

However, you might want to make sure your DHCP range on that router is setup correctly. You might benefit from using a scheme like:

router/gateway ip: 192.168.0.1 (or 192.168.1.1)
server ip: 192.168.0.50
dhcp range: 192.168.0.100 - 192.168.0.200 (or something similar)

then forward external 'wan' port 81 on the router to internal 192.168.0.50 private port 80. (to use dlink terminology). 

Looking at:
[http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/Echolink.htm](http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/Echolink.htm)
looks like you may not be able to do that, so you did the right thing having apache listen on port 81 on the server as well.

For your interfaces file, it looks okay to me as long as your router is actually 192.168.254.254

---

### Post by junapp on 2010-03-27
this tool may help you out a bit too.

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by jmr423 on 2010-03-28
solved it thanks everyone for your help.

i had to changed the virtual hosts to blank, listening port to 81,download the no-ip.com ubuntu client, forward my router to port 81 and forward the no-ip domain to myip:81


Note i still can not connect to my server through my external ip or domain name in my home network i have to go to a diferent network and connect.

---

