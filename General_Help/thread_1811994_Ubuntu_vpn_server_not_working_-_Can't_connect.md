---
title: "Ubuntu vpn server not working - Can't connect"
date: 2011-07-25
forum: General Help
---

### Post by Swirfin on 2011-07-25
Hi,

I have set up a computer with ubuntu server. I have tried installing vpn-server pptpd, but I can't get it to work over the internet. The server works fine over lan. 

The symptoms leads me to believe that there is a problem with

[LIST]
[*]my router
[*]the network that I connect from on the internet.
[/LIST]
I have a Cisco/Linksys E3000. For those familier with the router, I have enabled everything under security - VPN Passthrough. I have also forwarded the following ports to my server:
500 UDP,
1723 TCP, 
1701, TCP AND UDP.


I have tried to connect using two methods.

[LIST]
[*]Using my work computer to connect through mobile internet
[*]Having a friend try the connection from his home network.
[/LIST]
Both attempts yield somewhat interesting results:
The connection takes a long time, and fails after about 30 seconds. (we are both using win 7. he has also disabled firewall both on network and his router)

Even more interesting are what I can gather from the command:
netstat -anp | grep pptpd

If I run one netstat when I make a successfull connection from my LAN, and one when my friend tries to connect through the internet, the results are identical apart from our IP's. This leads me to believe that there is nothing wrong with neither my network or my friends.

Please advice on this issue. I'm sorry to say I'm a cmplete beginner in both linux and ubuntu.

On a side note:
I can connect successfully with the windows integrated VPN connection, but I can't seem to be able to connect using cisco anyconnect VPN. Why is this?

---

### Post by Kira_Belka on 2011-07-25
> **Swirfin said:**
> Hi,

I have set up a computer with ubuntu server. I have tried installing vpn-server pptpd, but I can't get it to work over the internet. The server works fine over lan. 

The symptoms leads me to believe that there is a problem with

[LIST]
[*]my router
[*]the network that I connect from on the internet.
[/LIST]
I have a Cisco/Linksys E3000. For those familier with the router, I have enabled everything under security - VPN Passthrough. I have also forwarded the following ports to my server:
500 UDP,
1723 TCP, 
1701, TCP AND UDP.


I have tried to connect using two methods.

[LIST]
[*]Using my work computer to connect through mobile internet
[*]Having a friend try the connection from his home network.
[/LIST]
Both attempts yield somewhat interesting results:
The connection takes a long time, and fails after about 30 seconds. (we are both using win 7. he has also disabled firewall both on network and his router)

Even more interesting are what I can gather from the command:
netstat -anp | grep pptpd

If I run one netstat when I make a successfull connection from my LAN, and one when my friend tries to connect through the internet, the results are identical apart from our IP's. This leads me to believe that there is nothing wrong with neither my network or my friends.

Please advice on this issue. I'm sorry to say I'm a cmplete beginner in both linux and ubuntu.

On a side note:
I can connect successfully with the windows integrated VPN connection, but I can't seem to be able to connect using cisco anyconnect VPN. Why is this?

cisco VPN is cisco vpn.. different protocols and etc.. did you think about Open-VPN server? clients?  openvpn.net ..I know also there are some clients for cisco vpn on linux

---

