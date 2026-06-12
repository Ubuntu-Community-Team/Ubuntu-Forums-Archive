---
title: "internet connection problem"
date: 2006-02-27
forum: General Help
---

### Post by noswal on 2006-02-27
My first experience with Linux  and it is installed and working. However I cant get my modem to work, or specifically an internet connection.

It is an IPW brand, usb connection, below outlines what I should do from another forum, but it didn't work as I probably have missed something:
-------------------
 

In /etc/ppp/peers create a file called 'sentech' with the following (substitute) :

noipdefault
/dev/ttyUSB0
115200
defaultroute
usepeerdns
hide-password
lcp-echo-interval 60
lcp-echo-failure 3
connect "/usr/sbin/chat -v -f /etc/ppp/peers/sentech-chat"
noauth
# persist
mtu 1400
user "username"
maxfail 1
deflate 15

In /etc/ppp/peers/sentech-chat create a file with the following :
TIMEOUT 30
ABORT "NO CARRIER"
ABORT "BUSY"
ECHO ON
SAY "Dialling sentech...\n"
"" \rAT
"OK-+++\c-OK" ATH0
OK ATZ
OK AT+CGDCONT=1,"PPP","sentech.co.za","username,password",0,0
OK ATD*99#
SAY "Waiting up 30 seconds for connection ... "
CONNECT ""

In /etc/ppp/chap-secrets create a file with the following (substitute) :
username * password *

Now run
pppd nodetach call sentech
------------------
I did write to the person who posted that (in another forum), but as yet no reply.  

I did enter my own username/passwords as directed.

Typing the run command given at the bottom  does nothing in terms of connection, eg firefox says there is no connection

I tried this command so the modem is recognized but missing something

tail /var/log/syslog

brian@Lps98:~$ tail /var/log/syslog
Feb 27 07:49:57 Lps98 kernel: [4333278.348000] usb 1-2: new full speed USB device using uhci_hcd and address 7
Feb 27 07:49:57 Lps98 kernel: [4333278.445000] usb 1-2: configuration #1 chosen from 2 choices
Feb 27 07:49:57 Lps98 kernel: [4333278.448000] ipwtty 1-2:1.0: IPWireless converter converter detected
Feb 27 07:49:57 Lps98 kernel: [4333278.452000] usb 1-2: IPWireless converter converter now attached to ttyUSB0
Feb 27 07:49:57 Lps98 usb.agent[18129]: Keeping default configuration with /sys//devices/pci0000:00/0000:00:1d.0/usb1/1-2
Feb 27 07:49:57 Lps98 usb.agent[18142]:      ipw: already loaded
Feb 27 07:50:07 Lps98 pppd[18194]: pppd 2.4.3 started by root, uid 0
Feb 27 07:50:08 Lps98 chat[18195]: timeout set to 30 seconds
Feb 27 07:50:08 Lps98 chat[18195]: abort on (NO CARRIER)
Feb 27 07:50:08 Lps98 chat[18195]: expect (^M)
brian@Lps98:~$



Any help, links, advice etc.

---

