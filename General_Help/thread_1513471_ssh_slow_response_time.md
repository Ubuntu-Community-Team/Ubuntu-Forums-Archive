---
title: "ssh slow response time"
date: 2010-06-19
forum: General Help
---

### Post by cent on 2010-06-19
When connecting to home ssh server behind a router on the internet there is a long delay before the connection is establish and it usually takes 1 minute from when I type something from it appears in the terminal (delays of up to 15 min have been observed). Both putty on windows and ssh on ubuntu 9.04 acts slow. A network tool shows that the server takes long time to respond. 

So far I have tried to disable reverse dns and GSSAPI* in the config to sshd.

---

### Post by cariboo on 2010-06-19
What do your ping times look like?

---

### Post by cent on 2010-07-04
I appology for the late reply but I appear to have fond the problem:
The wireless connection to the PC I'm connecting to is awfull
```
$ ping 192.168.1.105
PING 192.168.1.105 (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=3 ttl=64 time=563 ms
64 bytes from 192.168.1.105: icmp_seq=4 ttl=64 time=1.54 ms
64 bytes from 192.168.1.105: icmp_seq=8 ttl=64 time=68.5 ms
64 bytes from 192.168.1.105: icmp_seq=19 ttl=64 time=148 ms
64 bytes from 192.168.1.105: icmp_seq=27 ttl=64 time=181 ms
64 bytes from 192.168.1.105: icmp_seq=35 ttl=64 time=214 ms
64 bytes from 192.168.1.105: icmp_seq=40 ttl=64 time=182 ms
64 bytes from 192.168.1.105: icmp_seq=48 ttl=64 time=185 ms
64 bytes from 192.168.1.105: icmp_seq=56 ttl=64 time=224 ms
64 bytes from 192.168.1.105: icmp_seq=64 ttl=64 time=312 ms
^C
--- 192.168.1.105 ping statistics ---
65 packets transmitted, 10 received, 84% packet loss, time 64298ms
rtt min/avg/max/mdev = 1.545/208.405/563.449/143.162 ms

```

---

### Post by P1C0 on 2011-04-12
Hello!

I have a slow response time for ssh, it doesn't bother me much, but would really like to know what is causing it.

ssh -v user@host
```
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to host [XX.XXX.XX.XXX] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1

**[COLOR="red"]Delay_1[/COLOR]** (4-5 secs)

debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'host' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

**[COLOR="Red"]Delay_2[/COLOR]** (2-3 secs)

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Next authentication method: password
user@host's password: 

```

I fixed Delay_2 by setting UseDNS to no in the sshd_config file, but I can't fix Delay_1.

I tried commenting out the GSSAPI lines as suggested on the net, but didn't work..

Any ideas?

---

### Post by P1C0 on 2011-04-14
I managed to fix delay_1 too. The computer I was using to ssh into my desktop at home, didn't have a domain name, it didn't show up anywhere in the Logwatch log, just an IP adress.

I set up a domain name for that IP adress with dynDNS and now the ssh response from the desktop at home is instant.

> **P1C0 said:**
> Hello!

I have a slow response time for ssh, it doesn't bother me much, but would really like to know what is causing it.

ssh -v user@host
```
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to host [XX.XXX.XX.XXX] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1

**[COLOR=red]Delay_1[/COLOR]** (4-5 secs)

debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'host' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

**[COLOR=Red]Delay_2[/COLOR]** (2-3 secs)

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Next authentication method: password
user@host's password: 

```I fixed Delay_2 by setting UseDNS to no in the sshd_config file, but I can't fix Delay_1.

I tried commenting out the GSSAPI lines as suggested on the net, but didn't work..

Any ideas?

---

