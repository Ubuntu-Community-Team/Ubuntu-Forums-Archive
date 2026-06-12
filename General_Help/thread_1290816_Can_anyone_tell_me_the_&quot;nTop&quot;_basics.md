---
title: "Can anyone tell me the &quot;nTop&quot; basics?"
date: 2009-10-13
forum: General Help
---

### Post by rob86 on 2009-10-13
I just installed ntop, it looked like an interesting app to play with. I assume you start it with the command "sudo ntop -i ppp0" (ppp0 is my device) but after that, I see a whole load of output, warnings and everything.

I tried localhost:3000 and it indeed showed me a webpage of interesting stuff so I think it's working.

The last message is an ERROR, but it doesn't return me to the prompt, so I don't know if this error is "fatal' or just one of those errors I'm not supposed to care about.

A

Here's the output, it's pretty much all gibberish to me. Mostly, I just want to know if it looks like it's running okay. All the warnings and errors make me wonder. RRD Seems to be malfunctioning, I think I had to make a dir for it.

When I try to do admin stuff, it asks for a Username and Password, yet I never set one. Where do I set an admin password? 


```

Wed Oct 14 00:14:26 2009  NOTE: Interface merge enabled by default
Wed Oct 14 00:14:26 2009  Initializing gdbm databases
Wed Oct 14 00:14:26 2009  ntop will be started as user nobody
Wed Oct 14 00:14:26 2009  ntop v.3.3
Wed Oct 14 00:14:26 2009  Configured on Dec 23 2008 14:19:06, built on Dec 23 2008 14:19:28.
Wed Oct 14 00:14:26 2009  Copyright 1998-2007 by Luca Deri <deri@ntop.org>
Wed Oct 14 00:14:26 2009  Get the freshest ntop from http://www.ntop.org/
Wed Oct 14 00:14:26 2009  NOTE: ntop is running from 'ntop'
Wed Oct 14 00:14:26 2009  NOTE: (but see warning on man page for the --instance parameter)
Wed Oct 14 00:14:26 2009  NOTE: ntop libraries are in '/usr/lib'
Wed Oct 14 00:14:26 2009  Initializing ntop
Wed Oct 14 00:14:26 2009  Checking ppp0 for additional devices
Wed Oct 14 00:14:26 2009  Resetting traffic statistics for device ppp0
Wed Oct 14 00:14:26 2009  Initializing device ppp0 (0)
Wed Oct 14 00:14:26 2009  **WARNING** DLT: Device 0 [ppp0] MTU value unknown
Wed Oct 14 00:14:26 2009  **WARNING** DLT: Processing continues OK
Wed Oct 14 00:14:26 2009  DLT: Device 0 [ppp0] is 113, mtu 65355, header 0
Wed Oct 14 00:14:26 2009  Initializing gdbm databases
Wed Oct 14 00:14:28 2009  VENDOR: Loading MAC address table.
Wed Oct 14 00:14:28 2009  VENDOR: Checking for MAC address table file
Wed Oct 14 00:14:28 2009  VENDOR: File '/etc/ntop/specialMAC.txt' does not need to be reloaded
Wed Oct 14 00:14:28 2009  VENDOR: ntop continues ok
Wed Oct 14 00:14:28 2009  VENDOR: Checking for MAC address table file
Wed Oct 14 00:14:28 2009  VENDOR: File '/etc/ntop/oui.txt' does not need to be reloaded
Wed Oct 14 00:14:28 2009  VENDOR: ntop continues ok
Wed Oct 14 00:14:28 2009  Fingerprint: Loading signature file
Wed Oct 14 00:14:28 2009  Fingerprint: Checking for Fingerprint file... file
Wed Oct 14 00:14:28 2009  Fingerprint: Loading file '/etc/ntop/etter.finger.os'
Wed Oct 14 00:14:28 2009  Fingerprint: ...loaded 1765 records
Wed Oct 14 00:14:28 2009  ASN: Checking for Autonomous System Number table file
Wed Oct 14 00:14:28 2009  ASN: Loading file '/etc/ntop/AS-list.txt'
Wed Oct 14 00:14:28 2009  ASN: ...found 111435 lines
Wed Oct 14 00:14:28 2009  ASN: ....Used 3780 KB of memory (12 per entry)
Wed 14 Oct 2009 12:14:28 AM ADT  I18N: Default language (from ntop host) is 'en_CA'
Wed 14 Oct 2009 12:14:28 AM ADT  I18N: This instance of ntop supports 0 additional language(s)
Wed 14 Oct 2009 12:14:28 AM ADT  IP2CC: Checking for IP address <-> Country Code mapping file
Wed 14 Oct 2009 12:14:28 AM ADT  IP2CC: Loading file '/etc/ntop/p2c.opt.table'
Wed 14 Oct 2009 12:14:29 AM ADT  IP2CC: ...found 52395 lines
Wed 14 Oct 2009 12:14:29 AM ADT  Database support not compiled into ntop
Wed 14 Oct 2009 12:14:29 AM ADT  Initializing external applications
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3046509456]: NPA: network packet analyzer (packet processor) thread running [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3046509456]: NPA: Started thread for network packet analyzer (ppp0)
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3038116752]: SFP: Fingerprint scan thread starting [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3038116752]: SFP: Started thread for fingerprinting
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3029724048]: SIH: Idle host scan thread starting [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3029724048]: SIH: Started thread for idle hosts detection
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3021331344]: DNSAR(1): Address resolution thread running
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3021331344]: DNSAR(1): Started thread for DNS address resolution
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3012938640]: DNSAR(2): Address resolution thread running
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3012938640]: DNSAR(2): Started thread for DNS address resolution
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3004545936]: DNSAR(3): Address resolution thread running
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3004545936]: DNSAR(3): Started thread for DNS address resolution
Wed 14 Oct 2009 12:14:29 AM ADT  Calling plugin start functions (if any)
Wed 14 Oct 2009 12:14:29 AM ADT  SSL is present but https is disabled: use -W <https port> for enabling it
Wed 14 Oct 2009 12:14:29 AM ADT  INITWEB: Initializing web server
Wed 14 Oct 2009 12:14:29 AM ADT  INITWEB: Initializing TCP/IP socket connections for web server
Wed 14 Oct 2009 12:14:29 AM ADT  INITWEB: Initialized socket, port 3000, address (any)
Wed 14 Oct 2009 12:14:29 AM ADT  INITWEB: Waiting for HTTP connections on port 3000
Wed 14 Oct 2009 12:14:29 AM ADT  INITWEB: Starting web server
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2996153232]: WEB: Server connection thread starting [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  Note: SIGPIPE handler set (ignore)
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2996153232]: WEB: Server connection thread running [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  WEB: ntop's web server is now processing requests
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2996153232]: INITWEB: Started thread for web server
Wed 14 Oct 2009 12:14:29 AM ADT  Listening on [ppp0]
Wed 14 Oct 2009 12:14:29 AM ADT  Loading Plugins
Wed 14 Oct 2009 12:14:29 AM ADT  Searching for plugins in /usr/lib/ntop/plugins
Wed 14 Oct 2009 12:14:29 AM ADT  ICMP: Welcome to ICMP Watch. (C) 1999-2005 by Luca Deri
Wed 14 Oct 2009 12:14:29 AM ADT  LASTSEEN: Welcome to Host Last Seen. (C) 1999 by Andrea Marangoni
Wed 14 Oct 2009 12:14:29 AM ADT  **WARNING** Plugin '/usr/lib/ntop/plugins/lastSeenPlugin.so' contains a wrong filter specification
Wed 14 Oct 2009 12:14:29 AM ADT  **WARNING**     "ip or (vlan and ip)" on interface ppp0 (no VLAN support for data link type 113)
Wed 14 Oct 2009 12:14:29 AM ADT  The filter has been discarded
Wed 14 Oct 2009 12:14:29 AM ADT  NETFLOW: Welcome to NetFlow.(C) 2002-07 by Luca Deri
Wed 14 Oct 2009 12:14:29 AM ADT  PDA: Welcome to PDA. (C) 2001-2005 by L.Deri and W.Brock
Wed 14 Oct 2009 12:14:29 AM ADT  Remote: Welcome to Remote. (C) 2006-07 by L.Deri
Wed 14 Oct 2009 12:14:29 AM ADT  SFLOW: Welcome to sFlow.(C) 2002-04 by Luca Deri
Wed 14 Oct 2009 12:14:29 AM ADT  RRD: Welcome to Round-Robin Databases. (C) 2002-07 by Luca Deri.
Wed 14 Oct 2009 12:14:29 AM ADT  Calling plugin start functions (if any)
Wed 14 Oct 2009 12:14:29 AM ADT  RRD: Welcome to the RRD plugin
Wed 14 Oct 2009 12:14:29 AM ADT  RRD: Mask for new directories is 0700
Wed 14 Oct 2009 12:14:29 AM ADT  RRD: Mask for new files is 0066
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG: Parameters:
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpInterval 300 seconds
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpShortInterval 10 seconds
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpHours 72 hours by 300 seconds
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpDays 90 days by hour
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpMonths 36 months by day
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpDomains no
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpFlows no
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpHosts no
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpInterfaces yes
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpASs yes
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpMatrix no
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     dumpDetail high
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     hostsFilter 
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     rrdPath /var/lib/ntop/rrd
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     umask 0066
Wed 14 Oct 2009 12:14:29 AM ADT  RRD_DEBUG:     DirPerms 0700
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2987588496]: RRD: Data collection thread starting [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT: RRD: Started thread (t2987588496) for data collection
Wed 14 Oct 2009 12:14:29 AM ADT  INIT: Created pid file (/var/run/ntop.pid)
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3069839040]: ntop RUNSTATE: INITNONROOT(3)
Wed 14 Oct 2009 12:14:29 AM ADT  Now running as requested user 'nobody' (65534:65534)
Wed 14 Oct 2009 12:14:29 AM ADT  Note: Reporting device initally set to 0 [ppp0] (merged)
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3069839040]: ntop RUNSTATE: RUN(4)
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2979195792]: NPS(ppp0): pcapDispatch thread starting [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2979195792]: NPS(ppp0): pcapDispatch thread running [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t2979195792]: NPS(1): Started thread for network packet sniffing [ppp0]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3029724048]: SIH: Idle host scan thread running [p11775]
Wed 14 Oct 2009 12:14:29 AM ADT  THREADMGMT[t3038116752]: SFP: Fingerprint scan thread running [p11775]
Wed 14 Oct 2009 12:14:39 AM ADT  **ERROR** RRD: Disabled - unable to create base directory (err 13, /var/lib/ntop/rrd)
```

---

