---
title: "Can't Access Apache Server on the Local Network"
date: 2010-10-11
forum: General Help
---

### Post by texpat on 2010-10-11
I'm trying to set up a small Intranet system to run OpenERP or similar using browser-based clients. I have an Ubuntu machine running 10.04 desktop edition to act as a temporary/testing server until we set up a proper, dedicated machine with 10.04 server edition.

I have installed Apache2 from the repos and it is up and running fine - locally. That is the problem, I can't access the server from other machines on the LAN. Ping works, btw.

So I've been reading tutorials and howtos for the past week, but for the life of me, I can't find what I'm doing wrong. The standard Apache setup seems to be made to "just work", so although I've looked at the various configuration files mentioned in the tutorials, I haven't actually changed anything.

Therefore, dear members of the community, I turn to you asking for pointers and hints. You'll probably be wanting more information, but I'm not quite sure where to start, to be quite honest. I'm very much a noob when it comes to networking - and not much better at administration, either, I'm afraid.

Your help is, as always, greatly appreciated.

---

### Post by claydon on 2010-10-11
so on the linux machine you can browse to 127.0.0.1 and it works ? 
 
but when you browse to you linux machine from another machine on the network it doesnt work ?

---

### Post by texpat on 2010-10-11
Correct. I type 127.0.0.1 or the machine's IP 192.168.1.33 in the browser and the server responds "It works!...".

Typing the IP into the browser from another computer on the local network gets me "server not found."

As I mentioned, I can ping the IP address and get responses from it.

---

### Post by sidfadnis on 2010-10-13
well I have a similar problem. When I first installed apache2 all went fine, and I was able to access [http://localhost](http://localhost). The next day (after reboot) this page was not working. I checked and found that apache service was not started. So I issued this command "sudo /etc/init.d/apache2" and it errored out with message "make_sock can't bind to port 80. port in use" (or something similar.

I used netstat to see that "tcp6" was listening on port 80. I tried to kill "tcp6" but it did nothing. So I just changed the port in my conf files, and started apache. I set the new port to 1983. I could successfully start apache2 and access [http://localhost:1983](http://localhost:1983) 

The next day again the same problem happened, and this time this "tcp6" had attached to port 1983, causing apache2 to fail.

what is this tcp6 and how can I resolve this conflict between tcp6 and apach2.

thanks for helping out in advance.

---

### Post by texpat on 2010-10-15
Bump.. anyone?

---

### Post by Serpher on 2010-10-15
```
sudo apt-get install chkconfig
sudo chkconfig --level 5 httpd on
sudo init 6
```

Final command will restart your system.

---

### Post by bakegoodz on 2010-10-16
1. Is a firewall enabled on the server? If so is it setup correctly? Ubuntu comes with ufw firewall (maybe just on Ubuntu desktop?) type iptables -L on server and see what rules show up. If everything says "policy ACCEPT" then you have no firewall running.

2. Both computers on the same subnet? Example: Server 192.168.1.33 Desktop 192.168.1.29 (same first 3 octets if using 255.255.255.0 netmask)
If not on same subnet then then you have to have the correct routing, if using NAT you have to have port forwarding or DMZ for the server.

---

### Post by texpat on 2010-10-18
> **Serpher said:**
> ```
sudo chkconfig --level 5 httpd on
```

This responds with 'httpd: unknown service'

---

### Post by texpat on 2010-10-18
> **bakegoodz said:**
> 1. Is a firewall enabled on the server? If so is it setup correctly? Ubuntu comes with ufw firewall (maybe just on Ubuntu desktop?) type iptables -L on server and see what rules show up. If everything says "policy ACCEPT" then you have no firewall running.

I don't *think* there's a firewall, but here's the output of the [FONT="Courier New"]iptables -L[/FONT] command:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  192.168.0.0/24       anywhere            
ACCEPT     all  --  anywhere             192.168.0.0/24      
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination   
```

all machines have the same subnet mask.

Thanks for answering so far, guys. Keep 'em coming.

---

### Post by texpat on 2010-10-20
Rebump - hope this doesn't cause trouble, but I really need some help with this issue.

Cheers.

---

### Post by SeijiSensei on 2010-10-20
Let's start simply.  First flush those iptables rules away for the time being with "sudo iptables -F" then check with "sudo iptables -L -nv".  If iptables reports that any default policies are set to DROP, use "sudo iptables -P CHAIN ACCEPT" replacing "CHAIN" with "INPUT", "FORWARD", or "OUTPUT" as needed.  Now see if you can reach the web service.

If not, install a copy of nmap (from the repositories or [www.insecure.org](www.insecure.org)) on another machine and do a scan of the web server.  What ports are open?  Specifically can you see the server's port 80?  

> **texpat said:**
> This responds with 'httpd: unknown service'

The Apache server is called "httpd" on RedHat-flavored systems.  Use "sudo service apache2 restart" to restart the web server on Ubuntu.

---

### Post by texpat on 2010-10-21
[FONT="Courier New"]iptables -F[/FONT] executes OK.
[FONT="Courier New"]iptables -L -nv[/FONT] gives the following output:

```
Chain INPUT (policy ACCEPT 192 packets, 53434 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 65 packets, 5403 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-logging-deny (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-not-local (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
```

Still cannot connect to web server.

Installed nmap on another machine (W7, using Zenmap GUI frontend) and, what is really weird, I cannot see the machine at all. Reports [FONT="Courier New"]Host seems to be down. If it really is up, but blocking our ping probes, try -PN[/FONT], which I do with the same result. No scan gets through, not even ping. Ping from the command line, however, *does* get through.:confused:

---

### Post by texpat on 2011-06-22
OK, so I finally managed to solve this. This is for anyone stumbling onto this thread who may be facing similar issues.

Turns out the firewall was the culprit.

I ran 

```
sudo ufw --disable
```

simple as that... duh.

Now I have to re-set up iptables with sane settings, for which I'm using the info I found here:

[https://help.ubuntu.com/community/IptablesHowTo]("http://https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by innovator48 on 2011-10-20
If you are using windows, simply turn off the windows firewall setting from the control panel. The server should become accessible.

---

