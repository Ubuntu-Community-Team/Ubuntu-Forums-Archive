---
title: "openvpn error"
date: 2010-05-16
forum: General Help
---

### Post by r_s on 2010-05-16
I an unable to connect to an openvpn connection in ubuntu karmic. I have installed openvpn , I added the user certificate, CA certificate , Private key and the conf file in the /etc/openvpn directory.
Also followed the steps given here [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) under "Importing a Certificate into the System-Wide Certificate Authority Database" , but still when I try * openvpn --config linux_client.conf  *I get the following error.


Mon May 10 21:58:57 2010 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Mon May 10 21:58:57 2010 LZO compression initialized
Mon May 10 21:58:57 2010 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon May 10 21:58:57 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mon May 10 21:58:57 2010 Local Options hash (VER=V4): '41690919'
Mon May 10 21:58:57 2010 Expected Remote Options hash (VER=V4): '530fdded'
Mon May 10 21:58:57 2010 Socket Buffers: R=[114688->131072] S=[114688->131072]
Mon May 10 21:58:57 2010 UDPv4 link local: [undef]
Mon May 10 21:58:57 2010 UDPv4 link remote: 121.242.23.196:1194
Mon May 10 21:58:57 2010 TLS: Initial packet from 121.242.23.196:1194, sid=52e74c97 5c79acb5
Mon May 10 21:58:57 2010 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mon May 10 21:58:57 2010 VERIFY ERROR: depth=1, error=self signed certificate in certificate chain: /C=IN/ST=AP/L=Hyderabad/O=IIIT_Hyderabad/CN=vpn.iiit.ac.in/emailAddress=saurabh.barjatiya@iiit.ac.in
Mon May 10 21:58:57 2010 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Mon May 10 21:58:57 2010 TLS Error: TLS object -> incoming plaintext read error
Mon May 10 21:58:57 2010 TLS Error: TLS handshake failed
Mon May 10 21:58:57 2010 TCP/UDP: Closing socket
Mon May 10 21:58:57 2010 SIGUSR1[soft,tls-error] received, process restarting
Mon May 10 21:58:57 2010 Restart pause, 2 second(s)

---

### Post by r_s on 2010-05-17
Got a successful connection in fedora, but not in ubuntu . Any reasons.

---

### Post by iponeverything on 2010-05-17
> **r_s said:**
> Got a successful connection in fedora, but not in ubuntu . Any reasons.

You mean, besides the fact the two distributions are very different from each other? ;)

From your output we can see the handshake failed.

Take a look at the MTU that fedora was using with the successful connection.  

```
Mon May 10 21:58:57 2010 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Mon May 10 21:58:57 2010 TLS Error: TLS object -> incoming plaintext read error
Mon May 10 21:58:57 2010 TLS Error: TLS handshake failed
Mon May 10 21:58:57 2010 TCP/UDP: Closing socket

```

---

