---
title: "Confirm DNS Server"
date: 2011-03-23
forum: General Help
---

### Post by rowbird on 2011-03-23
Hi All, I changed my computer to use global DNS Server, but my router is set to use my ISP's DNS Server. How can I confirm the route? Thanks in advance.

---

### Post by conneco on 2011-03-23
that will show you which DNS server give you the IP which i think is what your after


```
host -v www.google.co.uk
```


else 

```
sudo apt-get install traceroute

traceroute www.google.co.uk
```

will show the route to a place but it wont give you any indication of what DNS server you got the IP from

hope this helps

Plus it wont matter what your routers set to it will use the PCS DNS settings, try wireshark if you want to be really sure

---

### Post by mike555 on 2011-03-23
Type this in terminal;     cat /etc/resolv.conf

---

### Post by rowbird on 2011-03-25
Hi, I tried your recommendation, but it seems complicated due to the fact that I can also set the DNS server on the modem. Which setting will override if I have the computer set on A global DNS server, and my router set on my ISP's DNS server?

---

### Post by dcstar on 2011-03-26
> **rowbird said:**
> Hi, I tried your recommendation, but it seems complicated due to the fact that I can also set the DNS server on the modem. Which setting will override if I have the computer set on A global DNS server, and my router set on my ISP's DNS server?

Your computer uses what is set in the **computer**, the router's setting is irrelevant.

---

### Post by rowbird on 2011-03-26
Thank you for clearing things up. I will just change my computer's DNS setting.

---

### Post by The Cog on 2011-03-26
It can be kind of complicated.

When a computer boots using DHCP (normally from the router), it can choose whether to use the DNS server given in the DHCP setup, or to ignore that and use a manually configured DNS server.

The router might learn the address of the DNS servers from the ADSL line as the connection comes up, or it might use servers configured locally on the router. In my router, it is a configuration option to use auto or manual DNS server settings.

Some routers will hand out the real DNS server addresses to the DHCP clients, other makes will give their own address as the DNS server, and then relay requests to the real DNS servers.

In all, the following are possible:
* DNS server manually configured in the PC
* Learned by DHCP, use the router as DNS server, router uses manually configured DNS server
* Learned by DHCP, use the router as DNS server, router uses servers learned from the ADSL line
* Learned by DHCP, use DNS servers manually configured in the router
* Learned by DHCP, use DNS servers that the router learned from the ADSL line

I believe that if you don't configure a DNS server in the Network Manager wizard, then it will use the server advertised by DHCP.

You can tell which DNS server is currently in use with the command nslookup, e.g. **nslookup [www.google.com](www.google.com)** which will tell you which server it used. 

You can also look in /etc/resolv.conf to see which servers are currently configured. But if you edit /etc/resolv.conf to change the server, bear in mind that Network Manager may re-write that file occasionally.

---

### Post by rowbird on 2011-03-27
Thanks for the detailed reply, but I am still having a problem understanding the output of both commands. Why would the output of  "cat /etc/resolv.conf" and "nslookup www.google.com" show the address of my gateway? Is it because I am using static IP addresses on my home network?

---

### Post by conneco on 2011-03-27
if you want to use a different DNS server such as googles public DNS server then the etc/reslov.conf should read something like this

```
nameserver 8.8.8.8
```

you may have to restart networking after editing the resolv.conf (i may be wrong but it cant hurt)

```
conneco@mcr-pc-29334:~$ sudo /etc/init.d/networking restart
```


then if you use nslookup [www.google.co.uk](www.google.co.uk) 

it should look like this

```
conneco@mcr-pc-29334:~$ nslookup www.google.co.uk
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
www.google.co.uk	canonical name = www.google.com.
www.google.com	canonical name = www.l.google.com.
Name:	www.l.google.com
Address: 74.125.230.112
Name:	www.l.google.com
Address: 74.125.230.113
Name:	www.l.google.com
Address: 74.125.230.115
Name:	www.l.google.com
Address: 74.125.230.116
Name:	www.l.google.com
Address: 74.125.230.114
```

bear in mind network manager changes this file when it starts so ever make the changes in nm or dont use nm atall

---

### Post by The Cog on 2011-03-27
> **rowbird said:**
> Thanks for the detailed reply, but I am still having a problem understanding the output of both commands. Why would the output of  "cat /etc/resolv.conf" and "nslookup www.google.com" show the address of my gateway? Is it because I am using static IP addresses on my home network?

This will be because, as I said, some routers will hand out the real DNS server addresses to the DHCP clients, other makes will give their own address as the DNS server, and then relay requests to the real DNS servers. It appears that your router is saying "Use me as the DNS server". It will of course be relaying the query to the real servers, but also caching the result so it can answer quicker next time. Your router should be able to tell you which DNS server it is using, somewhere in its status pages.

You can override what the PC does (I think) by editing the network manager config. Editing resolv.conf probably won't help because network manager re-writes it when it connects.

---

### Post by rowbird on 2011-03-27
Thanks for the reply, so it sounds like my router is responsible ultimately in assigning the DNS server. I have included a screenshot of my routers setup page.

---

### Post by SeijiSensei on 2011-03-27
You can tell the DHCP client in Ubuntu to ignore the router's DNS server information.  Use "sudo nano /etc/dhcp3/dhclient.conf" and remove the "domain-name," "domain-name-servers," and "domain-search" entries from the "request" directive.  Another alternative is to use the "prepend" directive to place other DNS servers ahead of the ones the router provides as the example in that file shows.

See "man dhclient.conf" for additional details.

---

### Post by rowbird on 2011-03-27
That's awesome. although in a network with multiple computers it is easier to just change the routers settings, so that it only need to be done once, as I upgrade often, I won't have to do it again every 6 months. Thanks again, for I am always amazed at the wealth of knowledge in this community.

---

### Post by SeijiSensei on 2011-03-27
In the long term, with multiple network users, you might be better off running [dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server") on a Linux box and disabling the router's DHCP server entirely.

---

### Post by rowbird on 2011-03-27
I think I have stumbled upon the reason why my samba shares don't show up on my "Windows Network" under Places in the main menu. The router is handling the DHCP serving, but that is another topic that I had posted without any replies. I will look into this further. Thanks for all the help guys.

---

### Post by SeijiSensei on 2011-03-27
Can you add static entries to the router's DNS server?  If so, maybe all you need is to do is add entries for any machines I doesn't add itself.  Most consumer routers expect to find Windows machines and know how to add the host's name when the address is given.  Sometimes running nmbd on your Samba box, if it's not running already, can help, and try adding the "netbios name" parameter to smb.conf.

One other thing to try is adding your hostname explicitly to the "send-hostname" parameter in dhclient.conf.

---

### Post by rowbird on 2011-03-27
My router is picking up my netbios name from my smb.conf file, and it is displayed under the status page in my router along side my static IP address that I set up in Wicd. Now all I need to do is get a name service to discover it, and broadcast it to my other computers.

---

