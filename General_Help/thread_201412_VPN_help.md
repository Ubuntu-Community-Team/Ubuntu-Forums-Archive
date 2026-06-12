---
title: "VPN help"
date: 2006-06-21
forum: General Help
---

### Post by jaymode on 2006-06-21
I have to VPN into my school when I access from an outstide network. They don't give me much help for nix. For Windows XP, Windows 2000, and Mac OSX they have instructions. I have installed network manager with PPTP VPN support from a repo I found on the forum. But I get a failue due to login failure.

I believe it has something to do with my /etc/ppp/chap-secrets file. I do not know how to set it up correctly.

From my school this is what I know:
[http://computing.vt.edu/internet_and_web/internet_access/vpn.html](http://computing.vt.edu/internet_and_web/internet_access/vpn.html)
From the Win 2k instructions:
Host name or Ip address: pptp.cns.vt.edu
Say to use this name: VT PPTP VPN
They want CHAP Encryption and CHAP V2 also
and it is a PPTP VPN

So I go through and set up through network manager.
Select PPTP Client
Connection Name: VT PPTP VPN
Gateway: pptp.cns.vt.edu
Username in the CHAP box: user (not real one of course)

SO then I need to edit the chap-secrets file:
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
VT PPTP VPN	user	pass		pptp.cns.vt.edu

And I get that error about login failure. I even changed my remote password to check it, but still get the error and can login in from windows.

---

### Post by localzuk on 2006-06-21
These are the instructions that Lancaster University use:

You need the programs "pptp-linux" and "pptpconfig" (check the repositories, or do a web search to find them). Once both are installed, run pptpconfig as root (or with sudo).

Fill in the following information:

    * Server
          o Name: Lancaster University VPN
          o Server: servername
          o Domain: (leave blank)
          o User name:
          o Password:
    * Routing
          o Tick the "All to Tunnel" box
    * DNS
          o Tick the "Automatic" box and leave the rest blank
    * Encryption
          o Tick the following:
          o Require Microsoft Point-to-Point encryption
          o Refuse 40-bit encryption
          o Refuse Stateless encryption
          o Refuse to Authenticate with EAP


The Miscellaneous tab settings should be left blank.

When all this is done, click the Add button and a new entry will appear in the Tunnel List window. To connect, click on this entry, then click the Start button, and you will be connected.

They use a similar setup I would believe.

---

### Post by jaymode on 2006-06-21
I followed those directions again and attempted before with this error:
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
Modem hangup
Connection terminated.
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1


BTW, I am attempting to connect through my wireless lan.

---

### Post by jaymode on 2006-06-22
bump for the morning

---

### Post by uteck on 2006-06-22
Is the MPPE option enabled in the kernel?  I know you used to have to patch and recompile the kernel to get it working, but I thought I read that it was finally incorperated into the kernel.

You can find out with somthing like this;
cat /boot/config.(kernel version) | grep MPPE

---

### Post by jaymode on 2006-06-22
[http://mppe-mppc.alphacron.de/](http://mppe-mppc.alphacron.de/)

I believe it has been finally added into the kernel. The last patch was for 2.6.13 and i have kernel 2.6.15-25 so I do no think that is a problem. But I will run that command when I get home.

---

### Post by jaymode on 2006-06-22
This is my output:
cat /boot/config-2.6.15-25-686 | grep MPPE
CONFIG_PPP_MPPE=m

---

### Post by jaymode on 2006-06-22
Ok I have figured it out. The defualt config refuses chap v1 and mschap authentication by default. You have to 
sudo gedit /etc/ppp/options.pptp

comment out 2 lines with refuse chap and refuse mschap or similar

Connect and it works. Hope this helps out others.

---

### Post by c-prompt on 2006-06-26
I also found out that if you uncheck and check the "require-mppe" in pptpconfig and check it again, the VPN will actually work.  This is the same glitch as jaymode described in the post above mine.

---

### Post by jizo on 2006-10-17
I have the same problem accept the fixed listed didn't do anything for me.  Can somebody please help as I can't connect to the VPN.

Funny thing is that I'm running windows 2003 server vmware image from ubuntu and from the windows 2003 image I can connect to the vpn no problem... but through ubuntu (host OS) I can seems to connect.  Here is my pptpconfig log any help would be greatly appreciated.

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option:
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>      Pass <number> to remote host as phone number
  --nolaunchpppd        Do not launch pppd, for use as a pppd pty
  --quirks <quirk>      Work around a buggy PPTP implementation
                        Currently recognised values are BEZEQ_ISRAEL only
  --debug               Run in foreground (for debugging with gdb)
  --sync                Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>      Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer            Disable packet buffering and reordering completely
  --idle-wait           Time to wait before sending echo request
  --max-echo-wait               Time to wait before giving up on lack of reply
  --logstring <name>    Use <name> instead of 'anon' in syslog messages
  --localbind <addr>    Bind to specified IP address instead of wildcard
  --loglevel <level>    Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux Jizolaptop 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-27-686/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-27-686 SMP preempt 686 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
Array
(
    [name] => <snip>
    [server] => <snip>
    [domain] =>
    [username] => <snip>
    [password] => (hidden by pptpconfig)
    [pppd-options] =>
    [pptp-options] =>
    [resolv] =>
    [dns-options] =>
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] =>
    [nomppe-128] =>
    [refuse-eap] =>
    [mppe-stateful] =>
    [autostart] =>
    [iconify] =>
    [persist] =>
    [debug] => 1
    [client-to-lan] =>
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.226.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.227.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug           # (from /etc/ppp/peers/Infuse)
updetach                # (from command line)
logfd 1         # (from command line)
linkname Infuse         # (from /etc/ppp/peers/Infuse)
dump            # (from /etc/ppp/peers/Infuse)
noauth          # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name jjohnson           # (from /etc/ppp/peers/Infuse)
remotename Infuse               # (from /etc/ppp/peers/Infuse)
                # (from /etc/ppp/options.pptp)
pty pptp 217.155.194.4 --nolaunchpppd           # (from /etc/ppp/peers/Infuse)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam Infuse          # (from /etc/ppp/peers/Infuse)
proxyarp                # (from /etc/ppp/options)
usepeerdns              # (from /etc/ppp/peers/Infuse)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe            # (from /etc/ppp/peers/Infuse)
require-mppe-128                # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 36
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xddef9e00> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp 217.155.194.4 --nolaunchpppd , pid 947
Script pptp 217.155.194.4 --nolaunchpppd  finished (pid 947), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.226.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.227.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.226.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.227.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

