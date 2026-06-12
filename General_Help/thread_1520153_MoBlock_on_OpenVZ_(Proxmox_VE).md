---
title: "MoBlock on OpenVZ (Proxmox VE)"
date: 2010-06-29
forum: General Help
---

### Post by fatfranko on 2010-06-29
I have a Proxmox VE OpenVZ host node.  I want to install MoBlock inside a Ubuntu Hardy container.  Unfortunately, it fails when starting.  Any help would be appreciated.  I can't find anything useful from google.  :(  I'm guessing I will have to do some kernel magic with my host node, which I never fiddled with before in fear of fubar'ing my host node.  I need this done though so I'm willing to risk it.  I made backups of all my vps's and I'm ready to ruin my week.

```

2010-06-28 06:02:35 PDT Begin: blockcontrol start
Building blocklist... Updating atma_atma... done.
Extracting atma_atma, detected 7z... done.
Updating Bluetack_ads... done.
Extracting Bluetack_ads, detected 7z... done.
Updating Bluetack_badpeers... done.
Extracting Bluetack_badpeers, detected 7z... done.
Updating Bluetack_bogon... done.
Extracting Bluetack_bogon, detected 7z... done.
Updating Bluetack_dshield... done.
Extracting Bluetack_dshield, detected 7z... done.
Updating Bluetack_forum-spam... done.
Extracting Bluetack_forum-spam, detected 7z... done.
Updating Bluetack_hijacked... done.
Extracting Bluetack_hijacked, detected 7z... done.
Updating Bluetack_iana-multicast... done.
Extracting Bluetack_iana-multicast, detected 7z... done.
 [33m*[39;49m /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 [33m*[39;49m wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
Updating Bluetack_iana-private... done.
Extracting Bluetack_iana-private, detected 7z... done.
Updating Bluetack_iana-reserved... done.
Extracting Bluetack_iana-reserved, detected 7z... done.
Updating Bluetack_level1... done.
Extracting Bluetack_level1, detected 7z... done.
Updating Bluetack_level2... done.
Extracting Bluetack_level2, detected 7z... done.
Updating Bluetack_level3... done.
Extracting Bluetack_level3, detected 7z... done.
Updating Bluetack_Microsoft... done.
Extracting Bluetack_Microsoft, detected 7z... done.
Updating Bluetack_proxy... done.
Extracting Bluetack_proxy, detected 7z... done.
Updating Bluetack_rangetest... done.
Extracting Bluetack_rangetest, detected 7z... done.
Updating Bluetack_spider... done.
Extracting Bluetack_spider, detected 7z... done.
Updating Bluetack_spyware... done.
Extracting Bluetack_spyware, detected 7z... done.
Updating Bluetack_web-exploit... done.
Extracting Bluetack_web-exploit, detected 7z... done.
Updating Bluetack_webexploit-forumspam... done.
Extracting Bluetack_webexploit-forumspam, detected 7z... done.
Updating cidr-report_bogon... done.
Extracting cidr-report_bogon, detected 7z... done.
Updating dchubad_faker... done.
Extracting dchubad_faker, detected 7z... done.
Updating dchubad_hacker... done.
Extracting dchubad_hacker, detected 7z... done.
Updating dchubad_pedophiles... done.
Extracting dchubad_pedophiles, detected 7z... done.
Updating dchubad_spammer... done.
Extracting dchubad_spammer, detected 7z... done.
Updating nexus23_ipfilterx... done.
Extracting nexus23_ipfilterx, detected 7z... done.
Updating peerblock_rapidshare... done.
Extracting peerblock_rapidshare, detected 7z... done.
Updating spamhaus_drop... done.
Extracting spamhaus_drop, detected 7z... done.
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

[86G[ OK ]
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-28 06:06:04 PDT Begin: blockcontrol start
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-28 06:06:34 PDT Begin: blockcontrol start
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-28 06:07:11 PDT Begin: blockcontrol stop
Stopping blockcontrol.wd
[86G[ OK ]
Deleting iptables ...
iptables v1.3.8: Couldn't load target `blockcontrol_in':/lib/iptables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_out':/lib/iptables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_fw':/lib/iptables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name

[86G[[31mfail[39;49m]
 [33m*[39;49m Don't worry! There occured some errors during the deletion of the iptables 
 [33m*[39;49m rules. The most common reason for this is that they did not exist, because
 [33m*[39;49m moblock was not running.
 [33m*[39;49m But if moblock was running there is some problem. Most probably you have
 [33m*[39;49m installed another firewall application that did delete the iptables rules.
 [33m*[39;49m A "blockcontrol restart" will then fix the situation.
Stopping moblock ...
[86G[ OK ]
2010-06-28 06:07:11 PDT End: blockcontrol stop
2010-06-28 06:07:15 PDT Begin: blockcontrol start
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-29 02:41:05 PDT Begin: blockcontrol start
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-29 02:54:03 PDT Begin: blockcontrol start
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!
2010-06-29 02:54:08 PDT Begin: blockcontrol restart
Stopping blockcontrol.wd
[86G[ OK ]
Deleting iptables ...
iptables v1.3.8: Couldn't load target `blockcontrol_in':/lib/iptables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_out':/lib/iptables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_fw':/lib/iptables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name

[86G[[31mfail[39;49m]
 [33m*[39;49m Don't worry! There occured some errors during the deletion of the iptables 
 [33m*[39;49m rules. The most common reason for this is that they did not exist, because
 [33m*[39;49m moblock was not running.
 [33m*[39;49m But if moblock was running there is some problem. Most probably you have
 [33m*[39;49m installed another firewall application that did delete the iptables rules.
 [33m*[39;49m A "blockcontrol restart" will then fix the situation.
Stopping moblock ...
[86G[ OK ]
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-2-pve/modules.dep: No such file or directory
 [31m*[39;49m Error 170: Could not load kernel module xt_NFQUEUE, not starting moblock!

```

---

### Post by jre on 2010-06-29
I don't know OpenVZ (Proxmox VE). But it definitely looks as if your kernel misses netfilter support. So you should make sure that the following kernel modules are either compiled directly in the kernel or are available as modules:
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
You can verify your kernel configuration in /boot/config-$(uname -r) (e.g. /boot/config-2.6.32-5-amd64). Note that this file only shows the configuration the kernel was built with. Simply editing this file is of no use therefore.

---

