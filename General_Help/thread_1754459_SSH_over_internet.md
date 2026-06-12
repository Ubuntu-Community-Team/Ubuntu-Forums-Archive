---
title: "SSH over internet"
date: 2011-05-10
forum: General Help
---

### Post by zoi0sooB on 2011-05-10
Hello,
I am currently attmpting to get SSH to work over the interet so my friends can access my Ubuntu 11.4 but i have hit a brick wall and dont know what to do...

Nomatter what happnes my friends putty ssh client just says 'connection timed out'. Im pretty sure its an issue on my end though...

Anyway, if it helps here is the ifconfig of the server

```


matthew@matthew-M720-US3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:2e:9c:5e
          inet addr:192.168.0.55  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe2e:9c5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60512 (60.5 KB)  TX bytes:63289 (63.2 KB)
          Interrupt:41 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```and this is the sshd_config
```

matthew@matthew-M720-US3:/etc/ssh$ sudo vi sshd_config
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 192.168.0.55
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no

```So, guys, Have i supplied enough information? What more must i do to get SSH to work over the interet (i have also forwared my port 22 to 192.168.0.55)

Also, i have tried looking around myself but i cant find any information relevent to my intrests.... If you guys could help, that would be great.

---

### Post by paulm23 on 2011-05-10
Everything looks OK in your setup.  Can you also list:

sudo iptables -L -n
route -n

Do you know if your ISP could be blocking inbound traffic?

Thnx,
Paul.

---

### Post by sj1410 on 2011-05-10
do you have a gateway in your ubuntu box of the router, to check if the port is open for public you use the following online tool

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by zoi0sooB on 2011-05-10
> **paulm23 said:**
> Everything looks OK in your setup.  Can you also list:

sudo iptables -L -n
route -n

Do you know if your ISP could be blocking inbound traffic?

Thnx,
Paul.

```


matthew@matthew-M720-US3:~$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


``````


matthew@matthew-M720-US3:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```
I dont think my ISP would be blocking anything, Ive never had a problem with that...

---

### Post by zoi0sooB on 2011-05-10
> **sj1410 said:**
> do you have a gateway in your ubuntu box of the router, to check if the port is open for public you use the following online tool

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

[img]http://mattcode.net/1337.PNG[/img]

Im not exactly sure how to fix this issue... also, i was looking at this website before too btw...

---

### Post by paulm23 on 2011-05-10
I've guess that your netgear box is at 192.168.0.1

Can you provide the output of:

sudo netstat -lpn

I've not used 11.04 yet.

Thnx,
Paul.

---

### Post by Aenima99x on 2011-05-10
> **famematt said:**
> [img]http://mattcode.net/1337.PNG[/img]

Im not exactly sure how to fix this issue... also, i was looking at this website before too btw...

I'd say that either your ISP is blocking port 22 or your router isn't forwarding it to your server (not likely based on your screenshot). Try using a different port to see if you can get it going. I use port 9 for my SSH. You'll need to change the port in your SSH config file and restart SSH and also change the port forward on your router.

---

### Post by Maheriano on 2011-05-10
Going to that IP is only going to get as far as your switch. You'll need to tell your switch which internal IP (computer) to forward the SSH request to when it comes in so that you can get all the way to the machine.

Once you set all this up you can give them a graphical desktop (if you want) with NoMachine's NXClient. That's what I use.

---

### Post by zoi0sooB on 2011-05-11
Thanks for the help guys, I changed putty and the SSH port to port 9 and it worked!

Thanks very much!

now.... how do i mark as solved? =D

Ohoop.
There we go...

---

### Post by Lars Noodén on 2011-05-11
> **famematt said:**
> ... I changed putty and the SSH port to port 9 and it worked!


See also [IANA's list of ports](http://www.iana.org/assignments/port-numbers) to see what the ports numers are usually used for.

---

