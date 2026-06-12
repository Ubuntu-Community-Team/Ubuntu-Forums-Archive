---
title: "Forwarding a connection with iptables"
date: 2011-03-15
forum: General Help
---

### Post by nkae100 on 2011-03-15
This is what I currently have in rc.local at the moment: 

> iptables -t nat -A PREROUTING -p tcp --dport 25 -j REDIRECT --to 2525 
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to 8080  I had been running my SMTP server with WINE, as the SMTP server is a Windows-based program (MERCURY), but I cracked the shits with WINE and removed it, so now I am going to run my SMTP server in a Windows virtual machine which has a different IP address than the host IP. 
The virtual machine is setup and ready, I can successfully telnet my mail server 192.168.56.101:25 from host. 
 
What I want though is for my computer (the host) to redirect traffic on port 25 to 192.168.56.101:2525. 
 
 
Based on what I can understand from what seems to be a thousand page, really, REALLY confusing iptables manual, I tried the following command, but it failed. 

> iptables -t nat -A -p tcp -s 10.1.1.3 -j -d 192.168.56.101  The problem I can see with the command above is that it fails to include instruction for ports. 
 
So, from an educated guess I tried this: 

> iptables -t nat -A -p tcp -s 10.1.1.3 --dport 25 -j -d 192.168.56.101 --dport 2525  ... and this: 
 
> iptables -t nat -A -p tcp -s 10.1.1.3:25 -j -d 192.168.56.101:2525  ... but these didn't work either. 
 
 
What I'm after is the magic iptables command. Could someone please help me with it?

---

### Post by nkae100 on 2011-03-16
Can someone PLEASE help me with this issue!

---

### Post by SeijiSensei on 2011-03-16
Did you enable IP forwarding in the kernel by editing /etc/sysctl.conf?  What is the result of typing "cat /proc/sys/net/ipv4/ip_forward"?  If it returns zero, forwarding is disabled (the default on most enduser-oriented distributions like Ubuntu). 

A quick test is to run the command:

```
echo '1' > /proc/sys/net/ipv4/ip_forward
``` 

and see if that fixes your problem.  If so, you need to activate the net.ipv4.ip_forward switch in /etc/sysctl.conf so forwarding will be enabled automatically at boot.

---

### Post by nkae100 on 2011-03-16
Cool, thanks.

But my problem is still not solved because my computer needs to forward incoming connections on port 25 to <IP> <PORT>.

---

### Post by SeijiSensei on 2011-03-17
It won't forward anything if packet forwarding is disabled in the kernel.

---

