---
title: "Stunnel Will Not Run - Please Help"
date: 2009-09-28
forum: General Help
---

### Post by hondcars on 2009-09-28
Hello All,
 
I am very very very very new to Ubuntu and I know nothing and I was wondering if any of you clever people can help me out. I want to use my ubuntu install to access newsgroups, I have a newsgroup server that uses SSL and I understand that "Stunnel" is needed in order to use SSL and Pan.
 
My newsgroup server requires a username and password, can you tell me how I input that please, do I do that in Pan?
 
 
I have installed Stunnel4 but for some reason I cannot get it to run (it just drops to the next line), my code is as follows:
 
```

; Sample stunnel configuration file by Michal Trojnara 2002-2006
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of chroot jail)
 
; Certificate/key is needed in server mode and optional in client mode
;cert = /etc/stunnel/mail.pem
;key = /etc/stunnel/mail.pem
 
; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3
 
; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
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
;debug = 7
;output = /var/log/stunnel4/stunnel.log
 
; Use it for client mode
client = yes
 
; Service-level configuration
[nntp]
accept = localhost:119
connect = secure.news.com:563
 
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
 
Then I try and run the following in terminal
 
```
 sudo /etc/init.d/stunnel4 start
```
 
an nothing happens. it just drops to the next line, I have also enabled Stunnel (not sure whats this about but I have done it anyway :))
 
```
/etc/default/stunnel4
```
 
and changed it to 1.

---

### Post by MonsterDuc on 2009-10-02
I think your port is wrong in your conf file, instead of 563, check your news servers webpage for what ports they are using SSL over.  Mine is 443.

---

