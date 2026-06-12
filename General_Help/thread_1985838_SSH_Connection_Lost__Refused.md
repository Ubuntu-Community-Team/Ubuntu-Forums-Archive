---
title: "SSH Connection Lost / Refused"
date: 2012-05-23
forum: General Help
---

### Post by julio8a00 on 2012-05-23
Hello,

I found a tutorial online on setting up Opensshd-server.
everything works fine when I try ssh user@localhost

but when I try to connect though another computer on the network it gives me:

Connection Lost
pool-my-ip-address.plspca.dsl-w.verizon.net/my.ip.address:22 - Connection Refused

i also tried different ports which I have forwarded on my router but it doesn't connect. I would really appreciate some help

thanks in advance

---

### Post by maverickaddicted on 2012-05-24
First check if you are able to ping the server or not from your local machine.
```
ping hostname or IP
```

If that works, try following things on server-

First check if the ssh is running on the server or not -

```
sudo service ssh status
```

Also check the default ssh port of the server if it is in listening or not

```
netstat -tuln
```

You can create following rule on iptables of server to allow the connections on port 22 (Default SSH Port)

```

iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

```

eth0 is network interface device, change it accordingly if you have something else like eth1, eth2....

---

### Post by roelforg on 2012-05-24
> **maverickaddicted said:**
> First check if you are able to ping the server or not from your local machine.
```
ping hostname or IP
```If that works, try following things on server-

First check if the ssh is running on the server or not -

```
sudo service ssh status
```Also check the default ssh port of the server if it is in listening or not

```
netstat -tuln
```You can create following rule on iptables of server to allow the connections on port 22 (Default SSH Port)

```

iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

```eth0 is network interface device, change it accordingly if you have something else like eth1, eth2....

Uh....  The service of opensshd is called sshd not ssh.

---

### Post by maverickaddicted on 2012-05-24
> **roelforg said:**
> Uh....  The service of opensshd is called sshd not ssh.
I use ssh only that's why I have written it like that - 
```

serveradmin@openserver:~$ sudo service sshd status
sshd: unrecognized service
serveradmin@openserver:~$ sudo service ssh status
ssh start/running, process 1063
serveradmin@openserver:~$ ssh -v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
serveradmin@openserver:~$ 

```

---

### Post by roelforg on 2012-05-24
> **maverickaddicted said:**
> I use ssh only that's why I have written it like that - 
```

serveradmin@openserver:~$ sudo service sshd status
sshd: unrecognized service
serveradmin@openserver:~$ sudo service ssh status
ssh start/running, process 1063
serveradmin@openserver:~$ ssh -v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
serveradmin@openserver:~$ 

```

I accidentally confused the service name with the deamon name (which *is* sshd).

---

### Post by maverickaddicted on 2012-05-24
> **roelforg said:**
> I accidentally confused the service name with the deamon name (which *is* sshd).

Thank You, I didn't know that.

---

### Post by roelforg on 2012-05-24
> **maverickaddicted said:**
> Thank You, I didn't know that.

Yeah, sshd is the deamon (it's short for ssh deamon) and ssh is the client.
Guess why i got confused.

---

### Post by julio8a00 on 2012-05-29
Thanks guys! this really helped, I got it to work.  =D

---

