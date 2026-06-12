---
title: "SSH VNC to Ubuntu through other computer?"
date: 2010-06-03
forum: General Help
---

### Post by PerfectReign on 2010-06-03
I would like to do the following. I had it working once a few years back but can't seem to find how I did it or what to use. (Googling is leading me nowhere.)

I have my home network exposed to the intraweb through my router on port 443. The router forwards 443 over to an older machine running Ubuntu 9.1.  I can login and use this system just fine.

I can create an ssh tunnel through which I proxy firefox (Namroka?) and that works.

I want to ssh into this computer and then VNC into a second computer, also running Ubuntu 9.1.  (I have vnc setup with a password on that computer and can access it when on the LAN.

What do I want to do?

---

### Post by Joe of loath on 2010-06-03
You would want to tunnel VNC through SSH. There should be some details here:

[http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/](http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/)

---

### Post by PerfectReign on 2010-06-03
That is a great article.

However, not exactly what I'm looking for.

IIRC, I was able to open some ssh tunnel to my home network: sudo ssh -C2qTnN -D 8080 [email]kai@my.home.ip.addy[/email]  

I'd then be able to use VNC (I generally use krdc.) to go to 127.0.0.1, which would point to my internal (at home) ip address of 192.168.0.102 (for example).

---

### Post by Joe of loath on 2010-06-03
Ah, OK I see. What I think you'll have to do is open up an SSH connection with the server, then use X forwarding for a VNC client on the server. There is probably a more elegant solution, but I don't know it.

---

### Post by bodhi.zazen on 2010-06-03
> **Joe of loath said:**
> Ah, OK I see. What I think you'll have to do is open up an SSH connection with the server, then use X forwarding for a VNC client on the server. There is probably a more elegant solution, but I don't know it.

No, not at all.

You use ssh -L or putty.

[http://bobpeers.com/linux/vnc_ssh.php](http://bobpeers.com/linux/vnc_ssh.php)

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Once you establish the tunnel, you vnc into localhost (127.0.0.1) using the post you designated with the link ( -L ).

You can speed up the VNC connection either by using blowfish to compress the data or FreeNX.

ssh -c arcfour,blowfish-cbc 

You may use additional options, such as -N if you wish.

---

### Post by PerfectReign on 2010-06-03
[UPDATE]

I found a site that had some information. [http://martybugs.net/smoothwall/sshvnc.cgi](http://martybugs.net/smoothwall/sshvnc.cgi)


I tried it out and am getting either a local screen or a blank screen.  Any ideas?

I have the transcript below. I put -v for verbose mode.  



> 
kai@kai-laptop:~/apps$ ssh -g -l kai -C -L 5901:192.168.0.100:5900 my.home.ip.addy -v
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to my.home.ip.addy [my.home.ip.addy] port 22.
debug1: Connection established.
debug1: identity file /home/kai/.ssh/identity type -1
debug1: identity file /home/kai/.ssh/id_rsa type -1
debug1: identity file /home/kai/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 [email]zlib@openssh.com[/email]
debug1: kex: client->server aes128-cbc hmac-md5 [email]zlib@openssh.com[/email]
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'my.home.ip.addy' is known and matches the RSA host key.
debug1: Found key in /home/kai/.ssh/known_hosts:4
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/kai/.ssh/identity
debug1: Trying private key: /home/kai/.ssh/id_rsa
debug1: Trying private key: /home/kai/.ssh/id_dsa
debug1: Next authentication method: password
[email]kai@my.home.ip.addy[/email]'s password:
debug1: Enabling compression at level 6.
debug1: Authentication succeeded (password).
debug1: Local connections to *:5901 forwarded to remote address 192.168.0.100:5900
debug1: Local forwarding listening on 0.0.0.0 port 5901.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on :: port 5901.
bind: Address already in use
debug1: channel 1: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux deathstar 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

76 packages can be updated.
47 updates are security updates.

Last login: Thu Jun  3 09:51:25 2010 from pc8130.temp2.co.la.ca.us
kai@deathstar:~$ debug1: Connection to port 5901 forwarding to 192.168.0.100 port 5900 requested.
debug1: channel 2: new [direct-tcpip]
channel 2: open failed: connect failed: No route to host
debug1: channel 2: free: direct-tcpip: listening port 5901 for 192.168.0.100 port 5900, connect from 127.0.0.1 port 50871, nchannels 3
debug1: Connection to port 5901 forwarding to 192.168.0.100 port 5900 requested.
debug1: channel 2: new [direct-tcpip]
channel 2: open failed: connect failed: No route to host
debug1: channel 2: free: direct-tcpip: listening port 5901 for 192.168.0.100 port 5900, connect from 127.0.0.1 port 50875, nchannels 3


---

### Post by bodhi.zazen on 2010-06-03
That looks fine, try connecting your VNC client to localhost:5900

---

