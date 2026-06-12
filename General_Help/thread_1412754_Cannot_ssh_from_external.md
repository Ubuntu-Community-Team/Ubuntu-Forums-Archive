---
title: "Cannot ssh from external"
date: 2010-02-21
forum: General Help
---

### Post by unix_user on 2010-02-21
Hi,
I installed Ubuntu 9.10 recently and registered with dyndns.org was able to ssh internally and from external.
a) ssh user@hostname  # hostname  worked fine
b) ssh -v [EMAIL="user@hostname.dyndns.xxx"]user@hostname.dyndns.xxx[/EMAIL]     worked fine.

Today, there were 200+ updates and after that I cannot ssh when I use the dyndns hostname, It stops after line
"connecting to hostname.dyndns.xxx [x.x.x.x] port 22

I checked site forums and checked /etc/ssh/ssh_config and sshd_config.  I use ufw and it allows port 22.

Can anyone suggest what may be stopping it to login.  I am guessing some updates may have caused it to stop.

Thanks in advance,

---

### Post by pbrane on 2010-02-21
Are you sure that your dyndns hostname still points to your actual IP? The other thing to try is restarting sshd.

---

### Post by unix_user on 2010-02-21
Here are things I checked
a) dyndns is pointing to updated IP, tried ssh to hostname and with ip
example: ssh -vvv [email]user@host.dyndns.xxx[/email]
ssh -vvv -p 22 [email]user@host.dyndns.xxx[/email]
ssh -vvv -p 22 user@99.x.x.x
It does not respond

b) tried restarting sshd 
sudo /etc/init.d/ssh restart   # shows Ok

c) System >  Administration > Firewall  [x] Enabled allows 22/tcp Allow Anywhere

d) ping host.dyndns.xxx     responds fine

e) sudo netstat -lnptu     # does not have any ssh entry - recollect seeing entry in past.

f) /etc/ssh/ssh_config has entry
Host *
  Port 22

g) removed the known_hosts file in my users home/.ssh


Anything else to check, 
Thanks

---

### Post by efflandt on 2010-02-21
Have you checked /var/log/messages on the machine you are trying to ssh to, to see if there is any sign of reaching it, or why it rejected the connection?

Is the PC you are trying to connect to behind a router with port 22 properly forwarded to it?

Are you actually testing it from the internet, or using its public name from a host on the same LAN?  Many routers do not do loopback (LAN2LAN via WAN IP).

---

### Post by unix_user on 2010-02-21
I am testing ssh commands this way (eventually login to home pc from external site)
Applications > Accessories > Terminal 
ssh user@localhost   # works fine
ssh -vvv [email]user@host.dyndns[/email].x  # waits and finally "connection refused"

I can see an entry in /var/log/messages each time I login, I can see
SRC=external IP as displayed by dyndns   DST=192.168.123.103 PROTO=TCP ...

I am checking the router settings, but I was able to reach host all of yesterday and today after applying updates I guess it is not allowing me to login.

I reinstalled ssh/firewall and it does not help,

Thanks for feedback and suggestions,

---

### Post by gmargo on 2010-02-21
Random ideas:

What is the whole entry from /var/log/messages?

"netstat -ln | grep :22" should show a listener on tcp port 22.  Is it listening on all interfaces or only localhost?

"ps -efw | grep ssh" should show a sshd process running.

Since you have "DST=192.168....." in the log message I can assume you're using a firewall device?  Is it configured properly to forward port 22?

Is local firewall software blocking?

---

### Post by unix_user on 2010-02-21
Now there is no entry in /var/log/messages, I see below output. I did reboot after my last post

a) ssh -v [email]user@hostname.dyndns.org[/email] output

OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx.xx.xx.xx [xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx port 22: Connection refused
ssh: connect to host xx.xx.xx.xx port 22: Connection refused

b) $ netstat -ln | grep :22
tcp        0      0 127.0.0.1:22            0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:22                  :::*                    LISTEN 

c) $ ps -efw | grep sshd
root      1350     1  0 18:41 ?        00:00:00 /usr/sbin/sshd
user    5519  5293  0 20:54 pts/1    00:00:00 grep --color=auto sshd

d) how to find out if local firewall is blocking

d) Firewall rules from Gufw 9.10.4
[x] Enabled    
    By Default [Allow]
4662/tcp ALLOW    Anywhere
4672/udp ALLOW     Anywhere
21/tcp    ALLOW    Anywhere
22/tcp     ALLOW     Anywhere

---

### Post by gmargo on 2010-02-22
The netstat output (enhanced here with column headers) shows the problem.
> 
```

$ netstat -ln | egrep ":22|Recv"
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 **127.0.0.1:22**            0.0.0.0:*               LISTEN     
tcp6       0      0 **::1:22**                  :::*                    LISTEN 

```The secure shell daemon is only listening on the _localhost_ interface.  Here's what it would look like if it was listening on all interfaces:

```

$ netstat -ln | egrep ":22|Recv"
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 **0.0.0.0:22**              0.0.0.0:*               LISTEN     
tcp6       0      0 **:::22**                   :::*                    LISTEN     

```So check the **ListenAddress** entry in **/etc/ssh/sshd_config**.

---

### Post by unix_user on 2010-02-22
Thanks gmargo for giving specific details on where problem could be, 
I will check **ListenAddress **later and let you all know.

---

### Post by 2hot6ft2 on 2010-02-22
When I set the Listen Address in sshd_config I was unable to connect to mine as well. Once I set it back to 0.0.0.0 and commented it out it worked fine again.
I suspect the same will be true for the ipv6 setting.

---

### Post by unix_user on 2010-02-22
Thanks everyone, I am able to connect now. 
Here are the changes made to /etc/ssh/sshd_config

Before
ListenAddress *
#ListenAddress 0.0.0.0

After
#ListenAddress *
ListenAddress 0.0.0.0

I did restart ssh and now I can connect.
sudo /etc/init.d/ssh restart.

Appreciate all the quick feedback from members. 
I have a backup of the config file to compare changes.

---

