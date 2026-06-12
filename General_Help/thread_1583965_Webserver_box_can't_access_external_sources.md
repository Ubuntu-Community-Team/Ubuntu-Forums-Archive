---
title: "Webserver box can't access external sources"
date: 2010-09-28
forum: General Help
---

### Post by zoomiest on 2010-09-28
Hello, I have googled and searched, but haven't seen a solution, so I am posting...

BACKGROUND:
I was trying to update my Ubuntu server (Ubuntu 8.04.3 LTS), and just got the error message: Could not resolve 'ca.archive.ubuntu.com'
This is my database server and webserver for my(small) company, and I don't want to screw this up.

INTERVENTIONS:
[LIST]
[*]So, I disabled my firewall (didn't make a difference)
[*]So, I unstalled my incomplete shorewall/mailserver installation, thinking was blocking things. (didn't make a difference)
[/LIST]

CURRENT STATE:
[LIST]
[*]The webserver functions normally. It resolves requests for my website. It resolves requests to upload resumes to jobs posted on my website. That seems to work fine.
[*]I can't get any responses to my pings to anything external, but it will ping the gateway router successfully.
[/List]

Here is my source.list, for your inspection.

```
#
# deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

I would think that the update server is down, except that I can't ping anything outside of my router...

Any help would be wonderful!

---

### Post by efflandt on 2010-09-28
Maybe something is acting up with ubuntu.com DNS.  At first the archive would not resolve, but their main website would.  After I did a dig for "any" and then "ns" the archive resolved:

**host ca.archive.ubuntu.com**
;; connection timed out; no servers could be reached

**host [www.ubuntu.com]("http://www.ubuntu.com")**
[www.ubuntu.com]("http://www.ubuntu.com") has address 91.189.89.88

**dig ca.archive.ubuntu.com any**

; <<>> DiG 9.7.1-P2 <<>> ca.archive.ubuntu.com any
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43654
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ca.archive.ubuntu.com.        IN    ANY

;; ANSWER SECTION:
ca.archive.ubuntu.com.    600    IN    A    91.189.88.40
ca.archive.ubuntu.com.    600    IN    A    91.189.88.46
ca.archive.ubuntu.com.    600    IN    A    91.189.92.166
ca.archive.ubuntu.com.    600    IN    A    91.189.88.31

;; Query time: 71 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Tue Sep 28 19:28:01 2010
;; MSG SIZE  rcvd: 103

**dig ca.archive.ubuntu.com ns**

; <<>> DiG 9.7.1-P2 <<>> ca.archive.ubuntu.com ns
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4904
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ca.archive.ubuntu.com.        IN    NS

;; AUTHORITY SECTION:
ubuntu.com.        3600    IN    SOA    ns1.canonical.com. hostmaster.canonical.com. 2010092901 10800 3600 604800 3600

;; Query time: 95 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Tue Sep 28 19:28:42 2010
;; MSG SIZE  rcvd: 100

**host ca.archive.ubuntu.com**
ca.archive.ubuntu.com has address 91.189.88.46
ca.archive.ubuntu.com has address 91.189.92.166
ca.archive.ubuntu.com has address 91.189.88.31
ca.archive.ubuntu.com has address 91.189.88.40

---

