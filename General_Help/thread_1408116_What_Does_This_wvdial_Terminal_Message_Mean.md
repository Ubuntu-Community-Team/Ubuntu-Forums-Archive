---
title: "What Does This wvdial Terminal Message Mean?"
date: 2010-02-16
forum: General Help
---

### Post by Mukoi on 2010-02-16
Hi,

Does anyone know what this terminal response means when I code: wvdial

[I]--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Feb 16 15:00:58 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2322
--> Using interface ppp0[/I]

I can still connect to the internet, but I am interested to know what the above response means.

---

### Post by plucky on 2010-02-16
> **Mukoi said:**
> Hi,

Does anyone know what this terminal response means when I code: wvdial

[I]--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Feb 16 15:00:58 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2322
--> Using interface ppp0[/I]

I can still connect to the internet, but I am interested to know what the above response means.

Read [Chap v PaP](http://tldp.org/LDP/nag/node120.html)

It probably means your wvdial.conf is not set up correctly for your Dialup modem.

See this [link](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?highlight=%28howto%29|%28modem%29)

Good Luck

---

