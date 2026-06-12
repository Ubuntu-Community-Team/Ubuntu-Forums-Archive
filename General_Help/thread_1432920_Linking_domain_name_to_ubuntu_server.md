---
title: "Linking domain name to ubuntu server"
date: 2010-03-18
forum: General Help
---

### Post by Sbarow on 2010-03-18
Hi,

I am very new to Ubuntu Server and Servers in general. I have a domain name registered with Enom and have access to the domain settings, what I want to know is there a way I can link my domain name (sbarow.com) to my Ubuntu server. I would like to be able to type my [http://www.sbarow.com](http://www.sbarow.com) into my browser as opposed to [http://ip_address](http://ip_address) to access my server from other locations. Any tutorials or advise on what to do would be greatly appreciated. Have searched this forum and Google but have no idea what I am looking for to be honest.

Thanks for your help.

---

### Post by pbrane on 2010-03-18
You need to have the server IP the same as the IP that your domain name is pointed to. If you ping your domain name you can see what address that is. I get two different IPs for sbarow.com and [www.sbarow.com](www.sbarow.com).

[http://ubuntuforums.org/showthread.php?t=465586]("http://ubuntuforums.org/showthread.php?t=465586")

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")

---

### Post by acroporas on 2010-03-18
You need to edit the DNS records for your domain.  Set the "A Record" to your IP address.

Then when you go to [http://yourdomainname.com](http://yourdomainname.com) you will be looking at your server - but it still might not work.  If that does not do it, you will need to add your domain name to apache's configuration.

---

### Post by Sbarow on 2010-03-18
Thanks guys. Okay I can link the domain name to the server. But I dont have a static ip address so I think it might get messed up sooner or later.

When I look at my host records they are:

Host Name         Address                   Record Type
@                         216.239.32.21       A (address)
@                         216.239.34.21       A (address)
@                         216.239.36.21       A (address)
@                         216.239.38.21       A (address)
calendar             ghs.google.com     CNAME (alias)
docs                    ghs.google.com     CNAME (alias)
mail                     ghs.google.com     CNAME (alias)
sites                    ghs.google.com     CNAME (alias)
start                    ghs.google.com     CNAME (alias)
www                    ghs.google.com     CNAME (alias)
(These details where set up when I bought the domain from google apps)

I know if I change the www address to my ip it connects to my server. Must I change all the above settings?

I want to get a static ip address, in one of the tutorial they mention that you must change the DHCP setting to Static and that you must add in details for:

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

Where do I find the correct details for my server? The details to enter into the above ie, address, netmask, network, broadcast and gateway?

---

### Post by acroporas on 2010-03-18
Ok, now I understand what you are trying to do.  This server is in your home?  The advise below all assumes the answer to this is yes.

Yes you will need to pay your ISP for a static IP address.  Otherwise, every time your ISP changes your IP address you website will break.  

If you are ok with the domain breaking every time your IP changes, you can find your current ip address by clicking this link. [http://www.ip-adress.com/](http://www.ip-adress.com/)  Then change your A record to the IP address that site gives you.  Every time your ip address changes you will have to go back and update the A record with your new IP address.

Alternatively to having domain break all of the time, if you don't/can't buy a static IP address from your ISP, you can pay for a dynamic dns service.  Look at your router's manual and see which (if any) dynamic dns services it supports and set up an account with them.  Then every time your IP address changes, your router will automatically contact the dynamic dns service provider who will then update your the dns accordingly.

Once you get that done, you will need to configure your local network.  You will have to set a static IP address for your server. This is a different IP address than the one you just dealing with.  It is an address on your local network. It does not really matter what you choose, you can choose anything in your local address space. For example you could set the servers IP address to 192.168.1.200  Then set your router to forward port 80 to the IP address you just set for your server. 

At that point traffic (on port 80) sent to your domain, will make it to your server.

---

