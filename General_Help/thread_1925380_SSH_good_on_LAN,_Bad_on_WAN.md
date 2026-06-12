---
title: "SSH good on LAN, Bad on WAN"
date: 2012-02-14
forum: General Help
---

### Post by CrusaderAD on 2012-02-14
I've seen a few posts, but no solutions to this. I installed openssh-server on my ubuntu server and I can connect on the LAN, no problem. This is the command I'm using:

```
ssh user@ipaddress
```

When I do it from a WAN I can make a connection just fine, it asks for a password and then denies me. Doesn't make sense, the user and password work fine on the LAN. Any ideas? Here's the debug info:

```
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 1.1.1.1 [1.1.1.1] port 22.
debug1: Connection established.
debug1: identity file /home/username/.ssh/id_rsa type -1
debug1: identity file /home/username/.ssh/id_rsa-cert type -1
debug1: identity file /home/username/.ssh/id_dsa type -1
debug1: identity file /home/username/.ssh/id_dsa-cert type -1
debug1: identity file /home/username/.ssh/id_ecdsa type -1
debug1: identity file /home/username/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.51
debug1: no match: dropbear_0.51
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Server host key: RSA 98:21:e7:31:5c:fa:08:51:f0:a0:b2:f8:37:4c:2a:15
debug1: Host '1.1.1.1' is known and matches the RSA host key.
debug1: Found key in /home/username/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/username/.ssh/id_rsa
debug1: Trying private key: /home/username/.ssh/id_dsa
debug1: Trying private key: /home/username/.ssh/id_ecdsa
debug1: Next authentication method: password
```

---

### Post by Lars Noodén on 2012-02-14
Are you sure you are connecting to the same machine in both cases?

---

### Post by CrusaderAD on 2012-02-14
> **Lars Noodén said:**
> Are you sure you are connecting to the same machine in both cases?

Yep, pretty sure. I don't have ssh running on any other machine and it does establish a connection just fine. Ports have been routed accordingly. FTP works just fine.

---

### Post by CrusaderAD on 2012-02-20
Bit of an update here. Now I just get a connection refused. Does the Ubuntu Server need to be configured in any special way to accept outside traffic on ssh? I think the firewall is setup just fine. So it must be the server refusing outside connections?

---

### Post by CrusaderAD on 2012-02-20
I tried some of the solutions in this tread:

[http://ubuntuforums.org/showthread.php?t=1032809]("http://ubuntuforums.org/showthread.php?t=1032809")

still doesn't work. Connection refused.

---

### Post by jonobr on 2012-02-21
Are you logging in as a 'regular' user?
Remote access root login would be treated differently and is all that comes to mind for me

---

### Post by Cheesehead on 2012-02-21
Ubuntu server requires no special WAN settings. If you can login from the LAN, then the server (including sshd and firewall settings) is configured correctly for login from the WAN also...

...assuming that your server is just another tenant on the LAN, and *that your router is properly configured to forward WAN ssh connections* to the server. The symptoms you describe could be a classic case of misconfigured router.

If, instead, your server is also the router, then your firewall rules need to be slightly more complex to deal appropriately with LAN vs WAN vs server traffic.

---

### Post by gsgleason on 2012-02-21
> debug1: Remote protocol version 2.0, remote software version dropbear_0.51
debug1: Server host key: RSA 98:21:e7:31:5c:fa:08:51:f0:a0:b2:f8:37:4c:2a:15


dropbear?  Compare the server host key from this output and verbose ssh connection from inside the lan.

---

### Post by Lars Noodén on 2012-02-22
[Dropbear](http://matt.ucc.asn.au/dropbear/dropbear.html) is often used in embedded devices, so it is possible that the WAN connection is not going through to the server but is connecting to the modem/router instead.

---

### Post by CrusaderAD on 2012-02-22
Thanks for all the replies. I was in the IRC and a bunch of people helped me conclude that it is indeed the firewall. It's a sonicwall. Weird thing is that I can FTP into the same server just fine. If I setup the same rules for port 22 SSH, I get a connection refused. Been driving me nuts.

---

### Post by CrusaderAD on 2012-02-22
I got it. It was an incorrect WAN ip setting configured in sonicwall. You need to setup a WAN address object with the correct WAN ip. Thanks for all the help!

---

