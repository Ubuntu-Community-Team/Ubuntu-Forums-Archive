---
title: "Cannot ssh after upgrade to 9.10"
date: 2009-12-22
forum: General Help
---

### Post by moody_mark on 2009-12-22
I have a two Pcs at home that ive upgraded from 9.04 to 9.10 in the last few weeks. All is working ok, except the other day I noticed I could not ssh to one from another. I can ping etc and the network connectivity seems fine. I have another PC running crunchbang Linux which i based on 9.04 I believe. I can ssh to this PC just fine.

As an example on the PC im typing this on Im running sshd;

```
curtis@Lisa:~$ ps aux | grep sshd
root      1370  0.0  0.0   5568   108 ?        Ss   Dec21   0:00 /usr/sbin/sshd
```

I can ssh to another pc just fine (some outpu truncated for brevity); 

```
curtis@Lisa:~$ ssh curtis@bart.local
curtis@bart.local's password: 
Linux Bart 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686

Last login: Sun Dec 20 11:38:09 2009 from homer.local

```

I can now try to ssh back to this PC from the remote one running crunchbang -but no dice;


```
curtis@Bart:~$ ping 192.168.0.10
PING 192.168.0.10 (192.168.0.10) 56(84) bytes of data.
64 bytes from 192.168.0.10: icmp_seq=1 ttl=64 time=0.384 ms
64 bytes from 192.168.0.10: icmp_seq=2 ttl=64 time=0.377 ms
64 bytes from 192.168.0.10: icmp_seq=3 ttl=64 time=0.363 ms
64 bytes from 192.168.0.10: icmp_seq=4 ttl=64 time=0.367 ms
^C
--- 192.168.0.10 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.363/0.372/0.384/0.025 ms
curtis@Bart:~$ ssh 192.168.0.10
```

What could be the problem, I cant seem to see anything in the /var/log/ directory that seemed to help?

Thanks

---

### Post by Rhubarb on 2009-12-22
That's an easy one to fix.

Firstly, make sure you've got the ssh server installed on the server (at a guess you'd have this anyway).

For the client PC, (ie the one machine where you type in ssh to connect to a remote computer):-
There's a directory that is presently storing the finger prints of all ssh servers that it's connected to in the past.  As you have upgraded one server, the finger print will be different, and hence your client will refuse to connect to it.

I'm sure there's a better way to do this, but this is what works for me:
Delete your ~/.ssh directory and its contents.

Then when you first connect to any ssh server, it'll prompt you to accept the finger print of the server pc (or key, or something along those lines).  Enter in "yes" and everything will work again.

---

### Post by moody_mark on 2009-12-22
> **Rhubarb said:**
> Firstly, make sure you've got the ssh server installed on the server....
I'm sure there's a better way to do this, but this is what works for me:
Delete your ~/.ssh directory and its contents.


Yes I have sshd installed (see the above sshd ps output)

I tried removing the .ssh/known_hosts file but the same problem;

```
curtis@Bart:~$ cd .ssh
curtis@Bart:~/.ssh$ ls
known_hosts
curtis@Bart:~/.ssh$ rm known_hosts 
curtis@Bart:~/.ssh$ cd ..
curtis@Bart:~$ ssh 192.168.0.10

```

Still no luck unfortunately, its almost like theres a firewall blocking the port, however theres no firewall running on either PC

---

### Post by Rhubarb on 2009-12-22
mmmm, maybe something got borked during the upgrade.
To rule this out, try running your server off live CD / USB, install the openssh server, and try to connect to it.

Failing that, it could be your openssh-server package needs to be reconfigured.
Or perhaps as you say, it may be a bizarre firewall issue.

Also note that you made a wee mistake:
> curtis@Bart:~$ ssh 192.168.0.10
- You need to add the user name you're connecting to in there (well I think you do, it might work I guess if you're logging into a server with the same username you're presently logged into).

---

### Post by moody_mark on 2009-12-23
> **Rhubarb said:**
> You need to add the user name you're connecting to in there (well I think you do, it might work I guess if you're logging into a server with the same username you're presently logged into).

correct the username on both machines is the same, otherwise you do need to use the syntax <user>@<host>.

Are you using ssh on 9.10 ok? Is this a known issue?

---

### Post by karthikkln on 2009-12-23
try to login with the ip num just like ssh 192.168.0.10
if still not connected go and sit in the particular pc in the root user, 
and in the terminal type this vi /root/.ssh/known_hosts
delete all the contents over there.. nw u connect the ssh it will be work..!

---

### Post by age99 on 2009-12-23
I'm running into the same problems after upgrading my sever to 9.10.  I try to connect via ssh, but the connection is refused.  

Running ssh localhost on the server was successful, but from the other machines I am getting no luck.  

Any ideas?

---

### Post by Rhubarb on 2009-12-23
Well, ssh works for for me in Karmic (9.10), but I've done clean installs of karmic, not upgrades.

That's why I suggest you try using a live CD / live USB just to confirm it's an upgrade issue.

---

### Post by age99 on 2009-12-23
I would like to avoid a complete re-install as there is yet no clear indication on what the problem is, and if the re-install will solve it.

---

### Post by slakkie on 2009-12-23
> **age99 said:**
> I would like to avoid a complete re-install as there is yet no clear indication on what the problem is, and if the re-install will solve it.

Little bit quick for a reinstall just because ssh is not properly working.

Try running ssh in verbose mode:
```

$ ssh -v yourhost
OpenSSH_5.1p1 Debian-8, OpenSSL 0.9.8k 25 Mar 2009               
debug1: Reading configuration data /etc/ssh/ssh_config           
debug1: Applying options for *                                   
debug1: Connecting to yourhost [ip.add.re.ss] port 22.    
debug1: Connection established.                                  
debug1: identity file /home/wesleys/.ssh/identity type -1        
debug1: identity file /home/wesleys/.ssh/id_rsa type 1           
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048      
debug1: identity file /home/wesleys/.ssh/id_dsa type 2           
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024      
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5
debug1: match: OpenSSH_5.1p1 Debian-5 pat OpenSSH*                                 
debug1: Enabling compatibility mode for protocol 2.0                               
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-8                        
debug1: SSH2_MSG_KEXINIT sent                                                      
debug1: SSH2_MSG_KEXINIT received                                                  
debug1: kex: server->client aes128-cbc hmac-md5 none                               

```

Try running tcpdump on both machines listening on port 22 if you think it is your network. You can write the dumps to file and look at it with wireshark.

On the server side you can start sshd on a different port in debug mode and test connecting to that.

---

### Post by moody_mark on 2009-12-23
> **Rhubarb said:**
> That's why I suggest you try using a live CD / live USB just to confirm it's an upgrade issue.

Sorry missed that suggestion above, I'll give that a try, good idea.

---

### Post by moody_mark on 2009-12-23
> **slakkie said:**
> Try running ssh in verbose mode:

It gets this far a times out

```
curtis@Bart:~$ ssh -v 192.168.0.10
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.10 [192.168.0.10] port 22.
debug1: connect to address 192.168.0.10 port 22: Connection timed out
ssh: connect to host 192.168.0.10 port 22: Connection timed out
```

Is there a sshd log somewhere? I cant seem to find it?

---

### Post by slakkie on 2009-12-23
Have a look in /var/log/auth.log: grep sshd /var/log/auth.log

I would also start using tcpdump to see if you see traffic going back and forth.

Can you do telnet yourhost 22?

---

### Post by moody_mark on 2009-12-24
Ok, so its good news at least, I tried the 9.10 Live CD, downloaded one last night and im writing this from the same PC running the live CD now. I can ssh to this PC ok now with the live CD (after installing ssh of course)

SSH from this PC to "Bart"

```
ubuntu@ubuntu:~$ ssh curtis@192.168.0.13
curtis@192.168.0.13's password: 
Linux Bart 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686


The programs included with CrunchBang Linux are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

CrunchBang Linux comes with ABSOLUTELY NO WARRANTY,
to the extent permitted by applicable law.

More information about CrunchBang Linux can be found at:
http://crunchbang.org/projects/linux/


26 packages can be updated.
44 updates are security updates.

Last login: Thu Dec 24 07:32:50 2009 from ubuntu.local

```

Now I ssh back from "Bart" to this PC

```
curtis@Bart:~$ ssh ubuntu@192.168.0.10
ubuntu@192.168.0.10's password: 
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

ubuntu@ubuntu:~$ 

```

I guess something got missed or deleted in the upgrade.

---

### Post by moody_mark on 2009-12-24
> **slakkie said:**
> Have a look in /var/log/auth.log: grep sshd /var/log/auth.log

I would also start using tcpdump to see if you see traffic going back and forth.

Can you do telnet yourhost 22?

I'l check those logs next and see, thanks. Do I need a particular service enabled for telnet, I cant remember if I need to enale a telnet daemon or not? Im confused, its still early ;-)

```
ubuntu@ubuntu:~$ telnet 192.168.0.10
Trying 192.168.0.10...
telnet: Unable to connect to remote host: Connection refused

```

---

### Post by age99 on 2009-12-30
It turns out the problem that I had was that the 9.10 upgrade gave my machine a new network address and all I had to do was to reset the port forwarding on the router.

I hope that helps somebody.

---

### Post by slakkie on 2009-12-30
> **moody_mark said:**
> I'l check those logs next and see, thanks. Do I need a particular service enabled for telnet, I cant remember if I need to enale a telnet daemon or not? Im confused, its still early ;-)

```
ubuntu@ubuntu:~$ telnet 192.168.0.10
Trying 192.168.0.10...
telnet: Unable to connect to remote host: Connection refused

```

No, telnet ip XX is the syntax for the telnet (application!) to connect to ip on port XX. So in my post I wanted to open a connection to the box on port 22 (which is used by ssh). You don't need to run telnetd (I discourage the usage of telnetd!).

---

### Post by moody_mark on 2009-12-30
Sorry! lol I didnt read your post fully

"telnet yourhost 22"

I tried to use port 22 but still no luck

```
curtis@Homer:~$ telnet 192.168.0.10 22
Trying 192.168.0.10...

```

Im going to try removing the ssh package completely from the machine and re-add to see if that might help. As I said before the live CD works fine

---

### Post by moody_mark on 2009-12-30
Ok I tried removing and installing the packages but no difference. I run a tcpdump on the target machine where the sshd is running **there was NO ssh entries on the auth.log** see outputs below. This problem is really strange, i seem to have all the correct packages installed, but its as if "Lisa" refuses to respond to the ssh requests from "Homer"

Only entries in the auth log were from the install of the ssh server

```
Dec 30 16:53:27 Lisa groupadd[2576]: group added to /etc/gshadow: name=ssh
Dec 30 16:53:28 Lisa groupadd[2576]: new group: name=ssh, GID=112
Dec 30 16:53:29 Lisa sshd[2651]: Server listening on 0.0.0.0 port 22.
Dec 30 16:53:29 Lisa sshd[2651]: Server listening on :: port 22.

```

TCP dump output on machine running sshd

```
curtis@Lisa:/var/log$ sudo tcpdump -v host Homer.local
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
16:54:41.971238 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 67)
    Homer.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 Homer.local. (Cache flush) A 192.168.0.15 (39)
16:54:47.133815 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 90)
    Homer.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 15.0.168.192.in-addr.arpa. (62)
16:54:47.855186 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has Lisa.local tell Homer.local, length 46
16:54:47.855235 ARP, Ethernet (len 6), IPv4 (len 4), Reply Lisa.local is-at 00:0f:b0:e0:87:dd (oui Unknown), length 28
16:54:47.857869 IP (tos 0x0, ttl 64, id 32165, offset 0, flags [DF], proto TCP (6), length 60)
    Homer.local.53385 > Lisa.local.ssh: Flags [S], cksum 0xdf22 (correct), seq 2177867020, win 5840, options [mss 1460,sackOK,TS val 8380585 ecr 0,nop,wscale 6], length 0
16:54:50.847284 IP (tos 0x0, ttl 64, id 32166, offset 0, flags [DF], proto TCP (6), length 60)
    Homer.local.53385 > Lisa.local.ssh: Flags [S], cksum 0xdc34 (correct), seq 2177867020, win 5840, options [mss 1460,sackOK,TS val 8381335 ecr 0,nop,wscale 6], length 0
16:54:56.847276 IP (tos 0x0, ttl 64, id 32167, offset 0, flags [DF], proto TCP (6), length 60)
    Homer.local.53385 > Lisa.local.ssh: Flags [S], cksum 0xd658 (correct), seq 2177867020, win 5840, options [mss 1460,sackOK,TS val 8382835 ecr 0,nop,wscale 6], length 0
16:55:08.842112 IP (tos 0x0, ttl 64, id 32168, offset 0, flags [DF], proto TCP (6), length 60)
    Homer.local.53385 > Lisa.local.ssh: Flags [S], cksum 0xcaa0 (correct), seq 2177867020, win 5840, options [mss 1460,sackOK,TS val 8385835 ecr 0,nop,wscale 6], length 0
```

---

### Post by moody_mark on 2009-12-31
Well what do you know, I had **ufw** configured!

```
curtis@Lisa:~$ sudo ufw status
Status: active

curtis@Lisa:~$ sudo ufw disable
Firewall stopped and disabled on system startup


curtis@Lisa:~$ ssh 192.168.0.13
curtis@192.168.0.13's password: 
Linux Bart 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686

Last login: Thu Dec 31 15:37:58 2009 from lisa.local
curtis@Bart:~$ ssh 192.168.0.10

curtis@192.168.0.10's password: 
Linux Lisa 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

Last login: Thu Dec 31 15:35:27 2009 from bart.local
```

Problem sorted!

---

