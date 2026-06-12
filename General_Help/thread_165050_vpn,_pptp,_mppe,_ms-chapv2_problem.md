---
title: "vpn, pptp, mppe, ms-chapv2 problem"
date: 2006-04-23
forum: General Help
---

### Post by [HUN]Levente on 2006-04-23
I want to connect to my university network via vpn, and it requires ms-chapv2.

I set up the connection, connection is ok, then I set ppp0 as the default route for packages to university ip addresses, but after this I cant reach the university ip-s, I can't even ping them, and then it discconects...

Log:

```
<user>@<host>:~$ sudo pon <name> debug dump logfd 2 nodetach
Password:
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options)
name <name>            # (from /etc/ppp/peers/<name>)
remotename pptp         # (from /etc/ppp/peers/<name>)
                # (from /etc/ppp/options)
pty pptp <ip> --nolaunchpppd          # (from /etc/ppp/peers/<name>)
-crtscts                # (from /etc/ppp/peers/<name>)
lcp-echo-failure 30             # (from /etc/ppp/peers/<name>)
ipcp-accept-remote              # (from /etc/ppp/peers/<name>)
ipparam schnet          # (from /etc/ppp/peers/<name>)
noipdefault             # (from /etc/ppp/peers/<name>)
nodefaultroute          # (from /etc/ppp/peers/<name>)
nodeflate               # (from /etc/ppp/options)
require-mppe-128                # (from /etc/ppp/peers/<name>)
using channel 13
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe10a19fd> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth chap MS-v2> <magic 0x65d5dac4> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth chap MS-v2> <magic 0x65d5dac4> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xe10a19fd> <pcomp> <accomp>]
rcvd [CHAP Challenge id=0x6c <56beefb01b50da124ed93a805d79d3c9>, name = "<name>"]
sent [CHAP Response id=0x6c <87b167ddd44cadb8e7da0b8ef214c5894400000000247d1592c5714bb1e5b6d16e8d0191e1dbc1a90f473bd76240b565b7>, name = "<name>"]
rcvd [CHAP Success id=0x6c "S=FE696035E52476DF32AF978615A231416DF8902F"]
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
sent [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr <ip>>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr <ip>>]
rcvd [IPCP ConfNak id=0x1 <addr <ip>>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr <ip>>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr <ip>>]
local  IP address <ip>
remote IP address <ip>
Script /etc/ppp/ip-up started (pid 21229)
Script /etc/ppp/ip-up finished (pid 21229), status = 0x0
Modem hangup
Connect time 2.0 minutes.
Sent 829926371 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 21268)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
Connection terminated.
Script pptp <ip> --nolaunchpppd finished (pid 21213), status = 0x0
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 21268
Script /etc/ppp/ip-down finished (pid 21268), status = 0x0
```

Can anyone help me what the problem could be?

I have a router before my computer with debian linux, and I don't use dhcp, I configured my connection manually to it, if this matters.

---

### Post by [HUN]Levente on 2006-04-24
No idea?

---

### Post by lxndr on 2006-04-25
Seams like there are a lot of people getting wild over the vpn issue, I'm on a university network also, but can't connect, solved several errors, it says it connects but it just wont... Had it working once, under Breezy, but it kept me on university pages only.

---

### Post by castironpants on 2008-02-12
I am have the EXACT same problem! Something has to be done about this! Who can we contact?

---

### Post by ebs16 on 2008-02-13
I'm also having a problem connecting to a PPTP ms-chap v2 network from linux.  I can connect with Windows XP's built-in VPN features with no problem.  Does anyone know how to make this work?

thanks!

---

