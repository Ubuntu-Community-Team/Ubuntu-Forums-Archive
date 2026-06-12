---
title: "Remote Access Windows XP from Ubuntu"
date: 2012-10-11
forum: General Help
---

### Post by hallartistry on 2012-10-11
Hi, so I am trying to access my brothers win xp laptop from my ubuntu laptop. I can do it successfully when I am at his house with both computers, I'm assuming because they are on the same internet connection, but when I get home and try it from my house, it won't connect. I've read a bit about port forwarding and all that, but I'm not sure at all how to do that or if I need to do that. Any suggestions?

---

### Post by dcstar on 2012-10-12
> **hallartistry said:**
> Hi, so I am trying to access my brothers win xp laptop from my ubuntu laptop. I can do it successfully when I am at his house with both computers, I'm assuming because they are on the same internet connection, but when I get home and try it from my house, it won't connect. I've read a bit about port forwarding and all that, but I'm not sure at all how to do that or if I need to do that. Any suggestions?

Search out the details for the incoming router and implement them for RDP port forwarding.

---

### Post by hallartistry on 2012-10-12
Well, I've gotten into my router settings(Netgear) and have set up a port forward using port 80 and my computer ip? Is that the ip I'm supposed to use, my computer's ip that I am trying to use to access my brother's computer?  
Anyway, it's still not working. I've tried different port numbers too.

---

### Post by efflandt on 2012-10-13
"Access" is an ambiguous term.  Are you trying to access files on his computer or use remote desktop (which would require that he have XP Pro).  It is your brother who would need to forward the necessary ports on his router to his computer, and you would have to know his public IP address to try to connect to it.  You cannot use computer names, because that requires a WINS server if not on the same LAN.

But opening Windows file and printer sharing onto the internet could be very risky and is how many worms and crackers get into computers.  So many ISP's block ports 137 - 139.

That or remote desktop passes through the internet unencrypted, so the remote desktop computer at our factory is isolated from the rest of our company network.

It would be better to use some sort of VPN connection (virtual private network) or tunnel through ssh.  But Windows does not have any native ssh server.

---

### Post by hallartistry on 2012-10-13
Remote desktop is what I meant, sorry. It seemed like from everything I've been reading, that I would need to forward ports from my end, but it would actually be from his end?  And I've read a bit about VNC and all that, but I can't seem to find info exactly for my situation. Seems like instructions are all going to be different for different computer set ups. I was hoping maybe there might be someone that has used their Ubuntu computer to remote access a Win XP computer desktop outside the network. It is Pro,  I was able to access it easily when on the same network.  I set the windows firewall on his computer to allow remote desktop also. It's frustrating because it doesn't seem like it should be this complicated.

---

