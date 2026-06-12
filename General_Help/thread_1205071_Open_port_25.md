---
title: "Open port 25"
date: 2009-07-05
forum: General Help
---

### Post by xiaomahe on 2009-07-05
hi, i want to setup my mail server for localhost, and i found out that port 25 is closed

i tried nmap, this is the result
 nmap -p 25 127.0.0.1

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-07-06 03:03 MYT
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns_servers
Interesting ports on localhost (127.0.0.1):
PORT   STATE  SERVICE
25/tcp closed smtp

i tried telnet, this is the result
telnet 127.0.0.1 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused


and of course that is what to expect if the port is closed,,

so, how do i open port 25 for my localhost?

I havent installed my mail server yet, so is it supposed to be close because no application listen to that port?

I tried iptables:
sudo iptables -A INPUT -p tcp -d 0/0 --dport 25 -j ACCEPT

but then, i use nmap and telnet, it still saying it is closed..

so, how do i open port 25??

---

### Post by kilowattradio on 2009-07-05
The port will be closed until you install and run the mail server or have any server on that port. There is nothing there to connect to so the ports *door* is shut until it is opened by a program.

---

### Post by xiaomahe on 2009-07-05
hai, i have tried installing postfix, and postfix should be listening to port 25 right??

but after i had installed and configure postfix by following this steup [https://help.ubuntu.com/8.10/serverguide/C/postfix.html](https://help.ubuntu.com/8.10/serverguide/C/postfix.html)

my port 25 is still closed.. i just want to setup for my localhost.

---

### Post by xiaomahe on 2009-07-05
hai, i have been getting replied that my postfix could not start up because of this

 fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied

what does this mean?

---

### Post by t4thfavor on 2009-07-05
postfix is probably already running, and it has a lock on that file.

I would keep reading about postfix until you get a little more familliar with both mail, and ports. 

A linux mailserver is fairly easy to understand once you have all the proper peices in place.

Look into iptables, or a gui for iptables such as webmin or firestarter.

---

### Post by MrWES on 2009-07-05
> **t4thfavor said:**
> postfix is probably already running, and it has a lock on that file.

I would keep reading about postfix until you get a little more familliar with both mail, and ports. 

A linux mailserver is fairly easy to understand once you have all the proper peices in place.

Look into iptables, or a gui for iptables such as webmin or firestarter.

the standard is now called ufw (uncomplicated firewall) and the GUI is gufw -- it's in the repos.

Bill

---

