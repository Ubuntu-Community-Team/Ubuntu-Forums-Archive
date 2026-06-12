---
title: "SSH Connection"
date: 2010-05-28
forum: General Help
---

### Post by oshirowanen on 2010-05-28
I wasn't to sure which forum to put this post in as it seems to fit into many sections, so I decided to stick it into the general section.  If I have made the wrong choice, I am sure the mods/admins  will deal with it.

Anyway, I am trying to connect to my home computer from my work computer via ssh.

My work computer is behind a hardware firewall which is already configured to allow the use of port 22/ssh.  I know I can use port 22 from work as I connect to an external web server daily using my work computer via ssh and it works perfectly by using the following command

ssh me@remote_server_ip_address

On my home computer, I have installed ssh_server, I have installed ufw and I think I have configured it properly to allow port 22 to be used.  At home I also have a linksys router, on which I think I have correctly configured it to allow me to use port 22.

But when I try to connect to my home computer from my work computer via

ssh me@home_computer_ip_address

I get the following message:

ssh: connect to host home_computer_id_address port 22: Connection timed out

What I am doing wrong?

Also, I can connect to the remote_server I mentioned before from my home computer, so ssh client seems to be working ok from my home computer.  I can also do

ssh localhost

from my home computer, and it allows me to connect OK.

Please help.

---

### Post by dino99 on 2010-05-28
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH](http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH)

---

### Post by geirha on 2010-05-28
Does ```
ssh me@external_ip_of_home_computer
``` work, from your home-computer?

---

### Post by Vishal Agarwal on 2010-05-28
try > telnet home_computer_ip 22 to be sure that the port is reachable to   incoming traffic. I guess.

---

### Post by lmarmisa on 2010-05-28
Are you sure that you have a static public IP address?. What do you mean with **ssh me@home_computer_ip_address**? **home_computer_ip_address** is your public IP address or a LAN address of type 192.168.x.y?.

Best regards,

Luis

---

### Post by oshirowanen on 2010-05-28
> **dino99 said:**
> [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH](http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH)

Thanks, I will read through these resources shortly.

> **geirha said:**
> Does ```
ssh me@external_ip_of_home_computer
``` work, from your home-computer?

I've not tried, I will try this as soon as I get home.

> **Vishal Agarwal said:**
> try  to be sure that the port is reachable to   incoming traffic. I guess.

I will try this also.  Thanks.

> **lmarmisa said:**
> Are you sure that you have a static public IP address?. What do you mean with **ssh me@home_computer_ip_address**? **home_computer_ip_address** is your public IP address or a LAN address of type 192.168.x.y?.

Best regards,

Luis

I got my IP address from whatismyip.com and it does not start with 192.168.X.Y

---

### Post by lmarmisa on 2010-05-28
If your ISP does not provide a static public IP address you will need to use a Dynamic DNS service like:

[http://www.dyndns.com/](http://www.dyndns.com/)

or

[http://www.no-ip.com/](http://www.no-ip.com/)

Some Linksys routers integrate the DDNS functions in their menus.

---

### Post by oshirowanen on 2010-05-28
I have a Linksys BEFSR41 router at home.

---

### Post by dino99 on 2010-05-28
> **oshirowanen said:**
> I have a Linksys BEFSR41 router at home.

so your /etc/resolv.conf might be filled with its ip (like nameserver 192.168.1.1, thats mine, set yours)

---

### Post by oshirowanen on 2010-05-28
> **dino99 said:**
> so your /etc/resolv.conf might be filled with its ip (like nameserver 192.168.1.1, thats mine, set yours)

Just to clarify, I need to change the IP Address in /etc/resolv.conf to mirror my home computers external IP Address?

---

### Post by lmarmisa on 2010-05-28
No, IMHO.

Could you type this command?

> 
ifconfig


---

### Post by lmarmisa on 2010-05-28
According to this manual

[http://support.radioshack.com/support_accessories/doc66/66591.pdf](http://support.radioshack.com/support_accessories/doc66/66591.pdf)

your router does not support any DDNS functionality.

---

### Post by geirha on 2010-05-28
Actually, try both internal and external ip.

```
ssh user@internal_ip
```
If that fails, check you firewall settings again.

```
ssh user@external_ip
```
if that fails, check the port forwarding on the router again.

If both work, it's likely the network at your work that blocks it.

---

### Post by lmarmisa on 2010-05-28
If you need to use Dynamic DNS, please, read this Ubuntu documentation:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by Serpher on 2010-05-28
You need this:

[http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by Vishal Agarwal on 2010-05-28
Just now found this very easy and interisting URL.
[http://sshmenu.sourceforge.net/articles/transparent-mulithop.html](http://sshmenu.sourceforge.net/articles/transparent-mulithop.html)

Read this. I have used just now to login one of my server through another server.

---

### Post by oshirowanen on 2010-05-28
Thank you for all the replies.  I will try all the suggestions tonight when I get home.

---

