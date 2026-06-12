---
title: "pgld/pglcmd not working"
date: 2011-01-17
forum: General Help
---

### Post by linwiz on 2011-01-17
hello, having some problems with pgld/pglcmd and need to figure out a fix. im running ubuntu on my cr-48 from[ this site]("http://chromeos-cr48.blogspot.com/2010/12/easy-way-to-install-ubuntu-on-your-cr.html")
uname: Linux cr48-ubuntu 2.6.32.23+drm33.10 #1 SMP Sat Jan 8 01:25:18 PST 2011 i686 GNU/Linux

it looks like a kernel issue but what can i do to fix it? this is using the chrome os kernel, and not ubuntu's kernel

 * Error 170: Could not load kernel module xt_NFQUEUE, not starting pgld!


```
2011-01-17 12:47:59 EST Begin: pglcmd start
Creating missing directory /var/spool/pgl ....
Creating missing directory /var/lib/pgl ....
Building blocklist... 
Updating Bluetack_dshield... done.
Extracting Bluetack_dshield, detected 7z... done.
Updating Bluetack_proxy... done.
Extracting Bluetack_proxy, detected 7z... done.
Updating TBG_Bogon... done.
Extracting TBG_Bogon, detected 7z... done.
Updating TBG_Business_ISPs... done.
Extracting TBG_Business_ISPs, detected 7z... done.
Updating TBG_General_Corporate_Ranges... done.
Extracting TBG_General_Corporate_Ranges, detected 7z... done.
Updating TBG_Hijacked... done.
Extracting TBG_Hijacked, detected 7z... done.
Updating TBG_Primary_Threats... done.
Extracting TBG_Primary_Threats, detected 7z... done.
Updating TBG_Search_Engines... done.
Extracting TBG_Search_Engines, detected 7z... done.
INFO: ASCII: 620986 entries loaded from "STDIN"
INFO: Merged 454037 of 620986 entries.
INFO: Blocklist has 166949 IP ranges (2969161102 IPs)

[152G[ OK ]
 * Error 170: Could not load kernel module xt_NFQUEUE, not starting pgld!
2011-01-17 12:51:04 EST Begin: pglcmd stop
Stopping pglcmd.wd
[152G[ OK ]
Deleting iptables ...

[152G[ OK ]
Stopping pgld ...
[152G[ OK ]
2011-01-17 12:51:04 EST End: pglcmd stop
2011-01-17 12:55:22 EST Begin: pglcmd start
Creating missing directory /var/spool/pgl ....
Building blocklist... 
Updating Bluetack_dshield... done.
Extracting Bluetack_dshield, detected 7z... done.
Updating Bluetack_proxy... done.
Extracting Bluetack_proxy, detected 7z... done.
Updating TBG_Bogon... done.
Extracting TBG_Bogon, detected 7z... done.
Updating TBG_Business_ISPs... done.
Extracting TBG_Business_ISPs, detected 7z... done.
Updating TBG_General_Corporate_Ranges... done.
Extracting TBG_General_Corporate_Ranges, detected 7z... done.
Updating TBG_Hijacked... done.
Extracting TBG_Hijacked, detected 7z... done.
Updating TBG_Primary_Threats... 2011-01-17 12:58:37 EST Begin: pglcmd update
Updating blocklists ...
Updating Bluetack_dshield... . No update available.
Extracting Bluetack_dshield, detected 7z... done.
Updating Bluetack_proxy... . No update available.
Extracting Bluetack_proxy, detected 7z... done.
Updating TBG_Bogon... . No update available.
Extracting TBG_Bogon, detected 7z... done.
Updating TBG_Business_ISPs... . No update available.
Extracting TBG_Business_ISPs, detected 7z... done.
Updating TBG_General_Corporate_Ranges... . No update available.
Extracting TBG_General_Corporate_Ranges, detected 7z... done.
Updating TBG_Hijacked... . No update available.
Extracting TBG_Hijacked, detected 7z... done.
Updating TBG_Primary_Threats... done.
Extracting TBG_Primary_Threats, detected 7z... done.
Updating TBG_Search_Engines... done.
Extracting TBG_Search_Engines, detected 7z... done.
Blocklists updated.
 * pgld is not running, doing nothing.
2011-01-17 13:02:03 EST End: pglcmd update
2011-01-17 13:04:41 EST Begin: pglcmd start
Building blocklist... 
INFO: ASCII: 620986 entries loaded from "STDIN"
INFO: Merged 454037 of 620986 entries.
INFO: Blocklist has 166949 IP ranges (2969161102 IPs)

[152G[ OK ]
 * Error 170: Could not load kernel module xt_NFQUEUE, not starting pgld!
```

---

### Post by jre on 2011-01-27
Sorry, I just spotted your thread.

Can you reconfigure and recompile your kernel? You have to enable netfilter support there. You need the following kernel modules (or compile them directly in the kernel):
```
iptable_filter
ip_tables
ipt_REJECT
nf_conntrack
nf_conntrack_ipv4
nf_defrag_ipv4
nfnetlink
nfnetlink_queue
x_tables
xt_iprange
xt_mark
xt_multiport
xt_NFQUEUE
xt_state
xt_tcpudp
```

Have a look here to learn how to build your own kernel: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Don't worry, building your own kernel is not hard.

Thus having said, please note that I don't know chrome os. Normally compiling your own kernel is no risk, because you can always choose your old kernel in grub (the bootloader). But after having a short look at the site that you mentioned this may not be possible with your installation. So I strongly recommend to ask in an appropriate forum, whether it is possible to recompile your chrome os kernel.

Or perhaps you can just install the Ubuntu kernel.

---

