---
title: "stunnel problem"
date: 2010-08-27
forum: General Help
---

### Post by noex869 on 2010-08-27
I'm trying to connect a server and clients via stunnel to do some  syslogging. I had this working with rsyslogs native tls but I need to  add some win boxes to the server.

I used ```
openssl req -new -x509 -days 3650 -nodes -out  stunnel.pem -keyout stunnel.pem 
``` to create the cert/key and these are my conf files

server
```

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/stunnel/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside the chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = zlib

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
; CApath = /certs
; It's often easier to use CAfile
; CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
; CRLpath = /crls
; Alternatively you can use CRLfile
; CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
;client = yes

; Service-level configuration

[ssyslog]
accept  = 60514
connect = 61514
```client

```
; Certificate/key is needed in server mode and optional in client mode

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside the chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[ssylog]
accept = 127.0.0.1:61514
connect = serverIP(censored):60514


```netstat shows that there are no established connections and there are some errors in the logs 

server - (can't find the logs matching the client)
```
 ssyslog accepted FD=13 from clientIP:46839
 ssyslog started
 FD 13 in non-blocking mode
 TCP_NODELAY option set on local socket
 Waiting for a libwrap process
 Acquired libwrap process #0
 Releasing libwrap process #0
 Released libwrap process #0
 ssyslog permitted by libwrap from clientIP:46839
 ssyslog accepted connection from clientIP:46839
 SSL state (accept): before/accept initialization
 SSL state (accept): SSLv3 read client hello A
 SSL state (accept): SSLv3 write server hello A
 SSL state (accept): SSLv3 write change cipher spec A
 SSL state (accept): SSLv3 write finished A
 SSL state (accept): SSLv3 flush data
 SSL state (accept): SSLv3 read finished A
    1 items in the session cache
    0 client connects (SSL_connect())
    0 client connects that finished
    0 client renegotiations requested
 1003 server connects (SSL_accept())
 1003 server connects that finished
    0 server renegotiations requested
 1002 session cache hits
    0 external session cache hits
    0 session cache misses
    0 session cache timeouts
 SSL accepted: previous session reused
 FD 14 in non-blocking mode
 connect_blocking: connecting 127.0.0.1:61514
 connect_blocking: s_poll_wait 127.0.0.1:61514: waiting 10 seconds
 connect_blocking: getsockopt 127.0.0.1:61514: Connection refused (111)
 Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
 ssyslog finished (0 left)
```client
```

 ssylog accepted FD=13 from 127.0.0.1:34016
 ssylog started
 FD 13 in non-blocking mode
 TCP_NODELAY option set on local socket
 Waiting for a libwrap process
 Acquired libwrap process #0
 Releasing libwrap process #0
 Released libwrap process #0
 ssylog permitted by libwrap from 127.0.0.1:34016
 ssylog accepted connection from 127.0.0.1:34016
 FD 14 in non-blocking mode
 connect_blocking: connecting serverIP:60514
 connect_blocking: s_poll_wait serverIP:60514: waiting 10 seconds
 connect_blocking: connected serverIP:60514
 ssylog connected remote server from clientIP:46839
 Remote FD=14 initialized
 TCP_NODELAY option set on remote socket
 SSL state (connect): before/connect initialization
 SSL state (connect): SSLv3 write client hello A
 SSL state (connect): SSLv3 read server hello A
 SSL state (connect): SSLv3 read finished A
 SSL state (connect): SSLv3 write change cipher spec A
 SSL state (connect): SSLv3 write finished A
 SSL state (connect): SSLv3 flush data
    1 items in the session cache
 1003 client connects (SSL_connect())
 1003 client connects that finished
    0 client renegotiations requested
    0 server connects (SSL_accept())
    0 server connects that finished
    0 server renegotiations requested
 1002 session cache hits
   0 session cache misses
    0 session cache timeouts
 SSL connected: previous session reused
 SSL_read: Connection reset by peer (104)
 Connection reset: 3902 bytes sent to SSL, 0 bytes sent to socket
 ssylog finished (0 left)

```from wire shark captures(77 is server and 12 is client) it looks like the client starts the connections  they shake hands negotiate the ssl tunnel then the client sends a  fin/ack and the server replies with a fin/ack.  But I have no idea why.

[IMG]http://i36.tinypic.com/25zi8w8.png[/IMG]

---

