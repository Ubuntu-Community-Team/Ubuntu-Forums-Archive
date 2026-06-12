---
title: "mgetty fails to accept faxes"
date: 2009-09-14
forum: General Help
---

### Post by tmazukna on 2009-09-14
Hi,

here is the sittuation:

Ubuntu  9.04 server.  mgetty  1.1.36
===============================================
mgetty log:
--------------------------------------------------------------------------------------------
09/14 22:52:28 yS0    select returned 1
09/14 22:52:28 yS0   checking lockfiles, locking the line
09/14 22:52:28 yS0   makelock(ttyS0) called
09/14 22:52:28 yS0   do_makelock: lock='/var/lock/LCK..ttyS0'
09/14 22:52:28 yS0   lock made
09/14 22:52:28 yS0  wfr: waiting for ``RING''
09/14 22:52:28 yS0   got: [0a][0d][0a]RING[0d]
09/14 22:52:28 yS0    CND: RING
09/14 22:52:28 yS0   wfr: rc=0, drn=0
09/14 22:52:28 yS0    CND: check no: 'none'
09/14 22:52:28 yS0  send: ATA[0d]
09/14 22:52:28 yS0  waiting for ``CONNECT''
09/14 22:52:28 yS0   got: ATA[0d]
09/14 22:52:28 yS0    CND: OKATA[0d][0a]+FHS:
09/14 22:53:09 yS0  found action string: ``+FHS:''
09/14 22:53:09 ##### failed A_FAIL dev=ttyS0, pid=6652, caller='none', conn='', name=''

=============================================================
mgetty.config
--------------------------------------------------------------------------------------------
debug 4

# set the local fax station id
fax-id  770-xxx-xxxx
# access the modem(s) with 38400 bps
#speed 38400
speed 19200

issue-file /etc/issue.mgetty

port ttyS0
  debug 9
#  data-only y
   fax-only y
   modem-type c2.0
   init-chat "" ATQ0V1H0 OK ATS0=0Q0&D3&C1 OK AT#CID=1 OK
   answer-chat "" ATA CONNECT \c \r

=============================================================
 
Modem is USR Courier.....
 
I cant figure out why mgetty would not go to receive fax when seeing FHS action.....
googled all evening and nothing....

please HELP.

thanks,
[COLOR=#888888]Tomas

[/COLOR]

---

### Post by tmazukna on 2009-09-15
It was init-chat script problem - modem was not negotiating the transfer speed.
here is the right config for receiving faxes with USR Courier:

=====================================================

port ttyS0
   debug 3
   modem-type auto
   rings 1
   init-chat "" ATQ0V1H0 OK AT#CID=1 OK AT&N0&B2&W&F1&D0S0=0 OK
   answer-chat "" ATA CONNECT \c \r
   autobauding yes

=================================================

AT&N0&B2&W

is the key here.... half an hour of RTFMing helped to pinpoint the problem.

Tomas

---

