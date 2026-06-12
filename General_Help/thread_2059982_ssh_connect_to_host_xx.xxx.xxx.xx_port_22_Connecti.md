---
title: "ssh: connect to host xx.xxx.xxx.xx port 22: Connection timed out"
date: 2012-09-19
forum: General Help
---

### Post by igorips on 2012-09-19
Need help im trying to open port 22 bt is still closed. Im open it on firewall . Can someone pls help me?

---

### Post by Lars Noodén on 2012-09-19
How did you open it on the firewall?  Is the firewall on the same machine as sshd?  If so, what are your firewall rules like?

```

sudo ufw status numbered

```

---

### Post by igorips on 2012-09-19
```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] OpenSSH                    ALLOW IN    Anywhere
[ 2] 22                         ALLOW OUT   Anywhere (out)
[ 3] OpenSSH (v6)               ALLOW IN    Anywhere (v6)
[ 4] 22                         ALLOW OUT   Anywhere (v6) (out)


```

Yes the firewall is on the same machine.

---

### Post by igorips on 2012-09-19
Someone help me pls ?

---

### Post by Lars Noodén on 2012-09-19
Can you connect from the same machine at all?

```
ssh -p 22 127.0.0.1
```

---

### Post by igorips on 2012-09-19
yes. Im open port 22 in the router. How to open port 22 ?? Its still closed :(

---

### Post by igorips on 2012-09-19
On localhost it works on another machine its connection timed out . Someone help?

---

### Post by igorips on 2012-09-19
Someone help me?

---

### Post by steeldriver on 2012-09-19
Some ideas

[LIST]
[*]start the ssh client with verbose option (ssh -v) - what does it say?
[*]look in the server's /var/log/auth.log - what does it say (for sshd)?
[/LIST]
Are you trying to connect from a machine on the same LAN or externally? if externally have you set up port forwarding on the router?

---

### Post by CharlesA on 2012-09-19
> **igorips said:**
> Someone help me?
Please only bump your threads once every 24 hours.

Thanks.

As for your problem - does it not work from another machine on the same network? My bet is port forwarding is either not set up right or your ISP is blocking port 22.

Try going to canyouseeme.org and see if it shows port 22 as open.

---

### Post by igorips on 2012-09-19
externaly
```

OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]

``` The log 
Sep 17 15:53:17 xxxx-xxx useradd[18454]: new user: name=sshd, UID=117, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Sep 17 15:53:18 xxxx-xxx usermod[18459]: change user 'sshd' password
Sep 17 15:53:18 xxxx-xxx chage[18464]: changed password expiry for sshd
Sep 17 15:53:18 xxxx-xxx sshd[18508]: Server listening on 0.0.0.0 port 22.
Sep 17 15:53:18 xxxx-xxx sshd[18508]: Server listening on :: port 22.

Im opening port 22 on the ruter in port forwarding.

---

### Post by Doug S on 2012-09-19
I think what Steeldriver meant was to try "ssh -v" while trying to connect. Example:```
doug@s16:~$ ssh -v s15.smythies.com
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to s15.smythies.com [192.168.111.112] port 22.
debug1: Connection established.
debug1: identity file /home/doug/.ssh/id_rsa type -1
...

```
You can also use telnet, just to check connectivity. Example:```
doug@s16:~$ telnet s15.smythies.com 22
Trying 192.168.111.112...
Connected to s15.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
Protocol mismatch.  [COLOR=red]<<< after typing the enter key, expected response[/COLOR]
Connection closed by foreign host.
doug@s16:~$

```We will try to help, but please answer the questions asked. Are you trying to connect from another machine on the same sub-net or from another machine from outside your local area network? It sounds like from outside your local area network from your reply above, where you said "external". Then definately try as CharlesA suggested, and I would agree with his bet that the issue is at the router and the port forwarding or your ISP blocks port 22.
 
Why do you have a user with the name sshd? That seems a bit odd to me.

---

### Post by CharlesA on 2012-09-19
I'm with Doug on this one.

```
Sep 17 15:53:17 xxxx-xxx useradd[18454]: new user: name=sshd, UID=117, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Sep 17 15:53:18 xxxx-xxx usermod[18459]: change user 'sshd' password
Sep 17 15:53:18 xxxx-xxx chage[18464]: changed password expiry for sshd
Sep 17 15:53:18 xxxx-xxx sshd[18508]: Server listening on 0.0.0.0 port 22.
Sep 17 15:53:18 xxxx-xxx sshd[18508]: Server listening on :: port 22.
```

That ^ doesn't look right. What user are you trying to login as? You should be able to use your normal username and password.

---

### Post by igorips on 2012-09-19
```

OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for localhost
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/linux/.ssh/identity type -1
debug1: identity file /home/linux/.ssh/identity-cert type -1
debug1: identity file /home/linux/.ssh/id_rsa type -1
debug1: identity file /home/linux/.ssh/id_rsa-cert type -1
debug1: identity file /home/linux/.ssh/id_dsa type -1
debug1: identity file /home/linux/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA bd:27:49:8f:05:65:fa:07:8e:f3:ec:fb:4d:bb:ec:9d
debug1: Host 'localhost' is known and matches the ECDSA host key.
debug1: Found key in /home/linux/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/linux/.ssh/identity
debug1: Trying private key: /home/linux/.ssh/id_rsa
debug1: Trying private key: /home/linux/.ssh/id_dsa
debug1: Next authentication method: password

```
Im trying to connect from the same machine ssh m.y.i.p.a.dd.r.e.ss bt the port is closed.

---

### Post by CharlesA on 2012-09-19
Does it do the same thing if you try to connect from another machine on the same network?

---

### Post by igorips on 2012-09-19
from another machine im canot connect. :/

---

### Post by Lars Noodén on 2012-09-20
What about connecting to the machine's external IP address from the machine itself?  You can find the IP address with ```

/sbin/ifconfig eth0
```

---

