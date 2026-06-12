---
title: "can't connect to VPN"
date: 2011-06-28
forum: General Help
---

### Post by proxikill on 2011-06-28
Hello,

I'm trying to setup an openVPN connection so I can acces my files outside my own network. I've successfully setup the port forwarding, and when I connect to my openVPN server I can see the following in the terminal:

```
Tue Jun 28 17:21:40 2011 us=560612 TCP/UDP: Closing socket
Tue Jun 28 17:21:41 2011 us=115465 MULTI: multi_create_instance called
Tue Jun 28 17:21:41 2011 us=115591 Re-using SSL/TLS context
Tue Jun 28 17:21:41 2011 us=115625 LZO compression initialized
Tue Jun 28 17:21:41 2011 us=115858 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Tue Jun 28 17:21:41 2011 us=115939 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Tue Jun 28 17:21:41 2011 us=116022 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-server'
Tue Jun 28 17:21:41 2011 us=116045 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-client'
Tue Jun 28 17:21:41 2011 us=116087 Local Options hash (VER=V4): 'c0103fa8'
Tue Jun 28 17:21:41 2011 us=116120 Expected Remote Options hash (VER=V4): '69109d17'
Tue Jun 28 17:21:41 2011 us=116203 TCP connection established with [AF_INET]192.168.1.1:58611
Tue Jun 28 17:21:41 2011 us=116236 TCPv4_SERVER link local: [undef]
Tue Jun 28 17:21:41 2011 us=116262 TCPv4_SERVER link remote: [AF_INET]192.168.1.1:58611
Tue Jun 28 17:21:42 2011 us=158022 192.168.1.1:58611 TLS: Initial packet from [AF_INET]192.168.1.1:58611, sid=4eb19dca b1daebcc
Tue Jun 28 17:21:42 2011 us=424634 192.168.1.1:58611 VERIFY ERROR: depth=0, error=unsupported certificate purpose: /C=BE/ST=BE/L=Antwerp/O=IC-it/CN=server/emailAddress=mail@kilianhendrickx.be
Tue Jun 28 17:21:42 2011 us=424856 192.168.1.1:58611 TLS_ERROR: BIO read tls_read_plaintext error: error:140890B2:SSL routines:SSL3_GET_CLIENT_CERTIFICATE:no certificate returned
Tue Jun 28 17:21:42 2011 us=424884 192.168.1.1:58611 TLS Error: TLS object -> incoming plaintext read error
Tue Jun 28 17:21:42 2011 us=424906 192.168.1.1:58611 TLS Error: TLS handshake failed
Tue Jun 28 17:21:42 2011 us=425042 192.168.1.1:58611 Fatal TLS error (check_tls_errors_co), restarting
Tue Jun 28 17:21:42 2011 us=425310 192.168.1.1:58611 SIGUSR1[soft,tls-error] received, client-instance restarting
Tue Jun 28 17:21:42 2011 us=425413 TCP/UDP: Closing socket

```This keeps repeating until I stop my laptop trying to connect.
My problem is that this is my first try to setup an openVPN installation, and I don't have any knowledge about it. I've folowed this tutorial: [http://www.basvandijk.eu/2009/01/27/openvpn-on-ubuntu-server-for-osx-clients-tutorial/](http://www.basvandijk.eu/2009/01/27/openvpn-on-ubuntu-server-for-osx-clients-tutorial/)

Is there a way I can get the installation working?

---

### Post by e79 on 2011-06-28
> Tue Jun 28 17:21:42 2011 us=424856 192.168.1.1:58611 TLS_ERROR: BIO read tls_read_plaintext error: error:140890B2:SSL routines:SSL3_GET_CLIENT_CERTIFICATE:no certificate returned

It seems that your client is not returning (or not having) the certificate asked by your server. are you sure you put all the required files (you should have created) in the same folder as your client.conf' ? These files should be 

[LIST]
[*]client.conf
[*]<username>.key
[*]<username>.crt
[*]ca.crt
[/LIST]

---

### Post by proxikill on 2011-06-29
I've uses "viscosity" for the VPN connection and selected the client.key  as keyfile, client.crt as Cert file and the CA.crt as CA.
I've noticed that the first error in the log is this: Wed Jun 29 13:59:37 2011 us=439983 192.168.1.1:61459 VERIFY ERROR:  depth=0, error=unsupported certificate purpose:  /C=BE/ST=BE/L=Antwerp/O=IC-it/CN=server/emailAddress=*my@email.adress*

Can that cause the problem?



This is my conf file:
```
# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one. On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server? Use the same setting as
# on the server.
proto tcp
;proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote myIP port
;remote my-server-2 1194

# Choose a random host from the remote
# list for load-balancing. Otherwise
# try hosts in the order specified.
;remote-random

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server. Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don&#8217;t need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nogroup

# Try to preserve some state across restarts.
persist-key
persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here. See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]

# Wireless networks often produce a lot
# of duplicate packets. Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description. It&#8217;s best to use
# a separate .crt/.key file pair
# for each client. A single ca
# file can be used for all clients.
ca ca.crt
cert client.crt
key client.key

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to &#8220;server&#8221;. This is an
# important precaution to protect against
# a potential attack discussed here:
# http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to &#8220;server&#8221;. The build-key-server
# script in the easy-rsa folder will do this.
;ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don&#8217;t enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20
```

---

### Post by e79 on 2011-06-29
I never used Viscosity to be honest,I am using the original OpenVPN client (on Linux and Windows). I noticed a discrepency cross-referencing my file with yours :

> 
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server
Yours is commented, so not used. In my setup (using PFSense firewall), I had to build the server key, I don't know if your setup required it (though I think it should). To do so, I followed this tutorial up to the part called 'Revoking Client Certificate' (because the rest differed for me as I am using PFSense).

Doing a quick research about your 'VERIFY ERROR:  depth=0, error=unsupported certificate purpose' error returned me :
[https://forums.openvpn.net/topic8258.html](https://forums.openvpn.net/topic8258.html)

So for some reason, maybe your certificate ended up wrong and it would worth a shot to try and redo them as they explain.

Hope this helps

---

