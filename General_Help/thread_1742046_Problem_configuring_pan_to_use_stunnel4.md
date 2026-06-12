---
title: "Problem configuring pan to use stunnel4"
date: 2011-04-28
forum: General Help
---

### Post by xeddog on 2011-04-28
I've been through a couple of tutorials about getting pan to work with stunnel but I guess I just haven't found the key yet.  If someone could help me out I'd appreciate it.  I don't know NEARLY enough about linux to even get started finding an answer.

So, I am running 64-bit Maverick and installed both pan and stunnel4 from synaptic. I went through the /etc/stunnel4/stunnel.conf file and it looks like this: (Note:  the "<---. . ." lines are added for info only and are not in the actual file)
```
; Sample stunnel configuration file by Michal Trojnara 2002-2009
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of the chroot jail)

; Certificate/key is needed in server mode and optional in client mode
;cert = /etc/ssl/certs/stunnel.pem
;key = /etc/ssl/certs/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3
delay = yes     <----  I have left this out, tried delay = no, and delay = yes

; Some security enhancements for UNIX systems - comment them out on Win32
;chroot = /var/lib/stunnel4/      <--------I have tried with this commented and uncommented
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
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7         <-------------I have tried with these two lines commented and uncommented, 
output = /var/log/stunnel4/stunnel.log  <----but the log file is always empty

; Use it for client mode
client = yes

; Service-level configuration

[nntp]
accept = localhost:119
connect = secure.usenetserver.com:563

;[pop3s]
;accept  = 995
;connect = 110

;[imaps]
;accept  = 993
;connect = 143

;[ssmtp]
;accept  = 465
;connect = 25

;[https]
;accept  = 443
;connect = 80
;TIMEOUTclose = 0


; vim:ft=dosini
```

When I start stunnel I get this:
```
$ service stunnel4 start
Starting SSL tunnels: 2011.04.28 12:51:35 LOG7[3531:140521117308672]: Snagged 64 random bytes from /dev/urandom
2011.04.28 12:51:35 LOG7[3531:140521117308672]: RAND_status claims sufficient entropy for the PRNG
2011.04.28 12:51:35 LOG7[3531:140521117308672]: PRNG seeded successfully
2011.04.28 12:51:35 LOG7[3531:140521117308672]: SSL context initialized for service nntp
2011.04.28 12:51:35 LOG3[3532:140521117308672]: setgid: Operation not permitted (1)
2011.04.28 12:51:35 LOG7[3531:140521117308672]: Snagged 64 random bytes from /dev/urandom
2011.04.28 12:51:35 LOG7[3531:140521117308672]: RAND_status claims sufficient entropy for the PRNG
2011.04.28 12:51:35 LOG7[3531:140521117308672]: PRNG seeded successfully
2011.04.28 12:51:35 LOG7[3531:140521117308672]: SSL context initialized for service nntp
2011.04.28 12:51:35 LOG3[3533:140521117308672]: setgid: Operation not permitted (1)
2011.04.28 12:51:35 LOG7[3531:140521117308672]: Snagged 64 random bytes from /dev/urandom
2011.04.28 12:51:35 LOG7[3531:140521117308672]: RAND_status claims sufficient entropy for the PRNG
2011.04.28 12:51:35 LOG7[3531:140521117308672]: PRNG seeded successfully
2011.04.28 12:51:35 LOG7[3531:140521117308672]: SSL context initialized for service nntp
2011.04.28 12:51:35 LOG3[3534:140521117308672]: setgid: Operation not permitted (1)
2011.04.28 12:51:35 LOG7[3531:140521117308672]: Snagged 64 random bytes from /dev/urandom
2011.04.28 12:51:35 LOG7[3531:140521117308672]: RAND_status claims sufficient entropy for the PRNG
2011.04.28 12:51:35 LOG7[3531:140521117308672]: PRNG seeded successfully
2011.04.28 12:51:35 LOG7[3531:140521117308672]: SSL context initialized for service nntp
2011.04.28 12:51:35 LOG3[3535:140521117308672]: setgid: Operation not permitted (1)
2011.04.28 12:51:35 LOG7[3531:140521117308672]: Snagged 64 random bytes from /dev/urandom
2011.04.28 12:51:35 LOG7[3531:140521117308672]: RAND_status claims sufficient entropy for the PRNG
2011.04.28 12:51:35 LOG7[3531:140521117308672]: PRNG seeded successfully
2011.04.28 12:51:35 LOG7[3531:140521117308672]: SSL context initialized for service nntp
2011.04.28 12:51:35 LOG3[3536:140521117308672]: setgid: Operation not permitted (1)
[Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file
$ 
```

And lastly when I try to do something with pan I get this in the pan event log:
```
Thu Apr 28 12:56:37 2011 - Pan 0.133 started
Thu Apr 28 12:56:37 2011 - Loaded data backend in 0.0 seconds
Thu Apr 28 12:56:50 2011 - Error connecting to "localhost" (Connection refused)
Thu Apr 28 12:56:52 2011 - Error connecting to "localhost" (Connection refused)
Thu Apr 28 12:56:57 2011 - Error connecting to "localhost" (Connection refused)
Thu Apr 28 12:57:02 2011 - Error connecting to "localhost" (Connection refused)
```


I hope it is something simple to fix, but it is beyond me at this point. 

Thanks,

Wayne

---

