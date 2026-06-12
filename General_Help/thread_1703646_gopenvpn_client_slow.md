---
title: "gopenvpn client slow"
date: 2011-03-09
forum: General Help
---

### Post by qwertyjjj on 2011-03-09
I have tried using the g openvpn client to connect to my OpenVPN server but it is very slow, it's almost as if the encryption algos are slow.
Any ideas?
When I connect with the normal Openvpn client on windows it works correctly.

Instead, I thought I could use openvpn on the command line but I cannot find any instructions about how to connect a client on Ubuntu.
j@j-Inspiron-9300:/etc/openvpn$ openvpn --config client.ovpn
Wed Mar  9 21:41:48 2011 OpenVPN 2.1.0 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Wed Mar  9 21:41:48 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Mar  9 21:41:48 2011 Cannot load private key file jw.jw.key: error:0200100D:system library:fopen:Permission denied: error:20074002:BIO routines:FILE_CTRL:system lib: error:140B0002:SSL routines:SSL_CTX_use_PrivateKey_file:system lib
Wed Mar  9 21:41:48 2011 Error: private key password verification failed
Wed Mar  9 21:41:48 2011 Exiting

---

