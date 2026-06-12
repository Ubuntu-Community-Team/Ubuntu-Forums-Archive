---
title: "MoBlock not working?"
date: 2010-06-27
forum: General Help
---

### Post by GrantStoner on 2010-06-27
Is moblock having issues right now? Every time I try to add the PPA software sources for moblock I get errors when refreshing it. I'm adding 
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main

and 

deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main

[FONT=Verdana]before I refresh.[/FONT]

---

### Post by jre on 2010-06-27
Works for me here.
Please verify that your sources.list is still intact after you added these entries.

---

### Post by GrantStoner on 2010-06-27
Where would I find my sources.list? And how do I verify that it's intact? What exactly am I looking for here? Unless something is noticeably wrong (i.e. it doesn't exist), I don't think I'd know if it's ok or not.

---

### Post by jre on 2010-06-28
It's /etc/apt/sources.list and any file that ends in ...sources.list in /etc/apt/sources.list.d/
Just post them here.

---

### Post by GrantStoner on 2010-06-28
The key seems to hang a bit for me, also. It tries to connect for about a minute before it tells me it timed out. after about 3 or 4 tries it gets it. But this the sources.list after I got the sources added finally. Moblock still won't start for me though. MoBloquer opens up but when I try to "start" it, it goes through the process and then says MoBlock isn't started and has a big red "X".
```
# 
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://archive.canonical.com/ lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
```

---

### Post by jre on 2010-06-28
Did you disable the automatic start of MoBlock?
Just press "Start" in mobloquer. The first start takes some time, because all blocklists need to be downloaded first.

Did you add my GPG key as described on [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) ?

---

### Post by GrantStoner on 2010-06-28
I did it as described on [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) but it looks to be about the same instructions, just Ubuntu formatted. When you say "the first start takes some time", is that longer than 15 minutes on a 3Mb/s connection? That's about how long I've been waiting thus far.

---

### Post by jre on 2010-06-28
You can follow the update process with "tail -f /var/log/blockcontrol.log". There you may also spot other errors.

EDIT: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) and [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) are both maintained by me and are nearly identical. Just make sure that you choose the **correct** GPG key for the Ubuntu packages in the PPA.

---

### Post by xenosaga456 on 2010-07-14
ya my moblock wont start ither ???

```
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
2010-07-13 11:51:42 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock ...   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 11:51:44 EDT End: blockcontrol restart
2010-07-13 12:52:32 EDT Begin: blockcontrol start
Inserting iptables ...
Allowing outbound traffic to DNS server 192.168.1.1
[74G[ OK ]
Allowing forwarded traffic to DNS server 192.168.1.1
[74G[ OK ]
Allowing loopback traffic
[74G[ OK ]

[74G[ OK ]
Starting moblock ...
[74G[ OK ]
Starting blockcontrol.wd ...
[74G[ OK ]
2010-07-13 12:52:32 EDT End: blockcontrol start
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
2010-07-13 12:57:32 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock ...   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 12:57:34 EDT End: blockcontrol restart
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
2010-07-13 13:42:36 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock ...   ...done.
Building blocklist...  * /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 * wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
 * Keeping old /var/spool/blockcontrol/Bluetack_iana-multicast/used/Bluetack_iana-multicast.
Updating nexus23_ipfilterx... done.
Extracting nexus23_ipfilterx, detected gz... done.
Updating /etc/blockcontrol/custom-blocklist.p2p...  *  Error 9: /etc/blockcontrol/custom-blocklist.p2p not available. Aborting!
2010-07-13 13:51:10 EDT Begin: blockcontrol start
Building blocklist...  * /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 * wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
 * Keeping old /var/spool/blockcontrol/Bluetack_iana-multicast/used/Bluetack_iana-multicast.
Updating /etc/blockcontrol/custom-blocklist.p2p...  *  Error 9: /etc/blockcontrol/custom-blocklist.p2p not available. Aborting!
2010-07-13 13:51:46 EDT Begin: blockcontrol start
Building blocklist...  * /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 * wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
 * Keeping old /var/spool/blockcontrol/Bluetack_iana-multicast/used/Bluetack_iana-multicast.
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 13:51:51 EDT End: blockcontrol start
2010-07-13 13:52:03 EDT Begin: blockcontrol update
Updating blocklists ...
Updating atma_atma... . No update available.
Extracting atma_atma, detected gz... done.
Updating Bluetack_ads... . No update available.
Extracting Bluetack_ads, detected gz... done.
Updating Bluetack_badpeers... . No update available.
Extracting Bluetack_badpeers, detected gz... done.
Updating Bluetack_bogon... . No update available.
Extracting Bluetack_bogon, detected gz... done.
Updating Bluetack_dshield... . No update available.
Extracting Bluetack_dshield, detected gz... done.
Updating Bluetack_edu... . No update available.
Extracting Bluetack_edu, detected gz... done.
Updating Bluetack_for-non-lan-computers... . No update available.
Extracting Bluetack_for-non-lan-computers, detected gz... done.
Updating Bluetack_forum-spam... . No update available.
Extracting Bluetack_forum-spam, detected gz... done.
Updating Bluetack_hijacked... . No update available.
Extracting Bluetack_hijacked, detected gz... done.
Updating Bluetack_iana-multicast... . No update available.
Extracting Bluetack_iana-multicast, detected gz... done.
Updating Bluetack_iana-private... . No update available.
Extracting Bluetack_iana-private, detected gz... done.
Updating Bluetack_iana-reserved... . No update available.
Extracting Bluetack_iana-reserved, detected gz... done.
Updating Bluetack_level1... . No update available.
Extracting Bluetack_level1, detected gz... done.
Updating Bluetack_level2... . No update available.
Extracting Bluetack_level2, detected gz... done.
Updating Bluetack_level3... . No update available.
Extracting Bluetack_level3, detected gz... done.
Updating Bluetack_Microsoft... . No update available.
Extracting Bluetack_Microsoft, detected gz... done.
Updating Bluetack_proxy... . No update available.
Extracting Bluetack_proxy, detected gz... done.
Updating Bluetack_rangetest... . No update available.
Extracting Bluetack_rangetest, detected gz... done.
Updating Bluetack_spider... . No update available.
Extracting Bluetack_spider, detected gz... done.
Updating Bluetack_spyware... . No update available.
Extracting Bluetack_spyware, detected gz... done.
Updating Bluetack_web-exploit... . No update available.
Extracting Bluetack_web-exploit, detected gz... done.
Updating Bluetack_webexploit-forumspam... . No update available.
Extracting Bluetack_webexploit-forumspam, detected gz... done.
Updating cidr-report_bogon... . No update available.
Extracting cidr-report_bogon, detected gz... done.
Updating dchubad_faker... . No update available.
Extracting dchubad_faker, detected gz... done.
Updating dchubad_hacker... . No update available.
Extracting dchubad_hacker, detected gz... done.
Updating dchubad_spammer... . No update available.
Extracting dchubad_spammer, detected gz... done.
Updating nexus23_ipfilterx... . No update available.
Extracting nexus23_ipfilterx, detected gz... done.
Updating spamhaus_drop... . No update available.
Extracting spamhaus_drop, detected gz... done.
Updating TBG_Bogon... . No update available.
Extracting TBG_Bogon, detected gz... done.
Updating TBG_Business_ISPs... . No update available.
Extracting TBG_Business_ISPs, detected gz... done.
Updating TBG_Educational_Institutions... . No update available.
Extracting TBG_Educational_Institutions, detected gz... done.
Updating TBG_General_Corporate_Ranges... . No update available.
Extracting TBG_General_Corporate_Ranges, detected gz... done.
Updating TBG_Hijacked... . No update available.
Extracting TBG_Hijacked, detected gz... done.
Updating TBG_Primary_Threats... . No update available.
Extracting TBG_Primary_Threats, detected gz... done.
Updating TBG_Search_Engines... . No update available.
Extracting TBG_Search_Engines, detected gz... done.
Blocklists updated.
Problematic daemon status: 1
 * moblock is not running
2010-07-13 13:56:03 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13170: No such process
   ...done.
Building blocklist...  * /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 * wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
 * Keeping old /var/spool/blockcontrol/Bluetack_iana-multicast/used/Bluetack_iana-multicast.
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 13:56:09 EDT End: blockcontrol restart
2010-07-13 13:56:42 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 13:59:43 EDT Begin: blockcontrol stop
Stopping blockcontrol.wd
[74G[ OK ]
Deleting iptables ...

[74G[ OK ]
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18101: No such process

[74G[ OK ]
2010-07-13 13:59:44 EDT End: blockcontrol stop
2010-07-13 14:01:27 EDT Begin: blockcontrol start
Inserting iptables ...
Allowing loopback traffic
[74G[ OK ]

[74G[ OK ]
Starting moblock ...
[74G[ OK ]
Starting blockcontrol.wd ...
[74G[ OK ]
2010-07-13 14:01:27 EDT End: blockcontrol start
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
2010-07-13 14:02:38 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:04:38 EDT Begin: blockcontrol stop
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2469: No such process
   ...done.
2010-07-13 14:04:38 EDT End: blockcontrol stop
2010-07-13 14:05:00 EDT Begin: blockcontrol start
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:05:01 EDT End: blockcontrol start
2010-07-13 14:05:23 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:07:20 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:07:56 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:09:14 EDT Begin: blockcontrol stop
Stopping blockcontrol.wd
[74G[ OK ]
Deleting iptables ...

[74G[ OK ]
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4642: No such process

[74G[ OK ]
2010-07-13 14:09:14 EDT End: blockcontrol stop
2010-07-13 14:11:47 EDT Begin: blockcontrol start
Inserting iptables ...
Allowing loopback traffic
[74G[ OK ]

[74G[ OK ]
Starting moblock ...
[74G[ OK ]
Starting blockcontrol.wd ...
[74G[ OK ]
2010-07-13 14:11:48 EDT End: blockcontrol start
2010-07-13 14:13:21 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:13:30 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:13:51 EDT Begin: blockcontrol stop
Stopping blockcontrol.wd
[74G[ OK ]
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.

[74G[[31mfail[39;49m]
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2382: No such process

[74G[ OK ]
2010-07-13 14:13:51 EDT End: blockcontrol stop
2010-07-13 14:31:00 EDT Begin: blockcontrol stop
Stopping blockcontrol.wd
[74G[ OK ]
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.

[74G[[31mfail[39;49m]
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock ...
[74G[ OK ]
2010-07-13 14:31:00 EDT End: blockcontrol stop
2010-07-13 14:37:54 EDT Begin: blockcontrol start
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:37:54 EDT End: blockcontrol start
2010-07-13 14:39:50 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:42:53 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:42:54 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6681: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:42:55 EDT End: blockcontrol restart
2010-07-13 14:43:16 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:44:01 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:47:55 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 9829: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:47:55 EDT End: blockcontrol restart
2010-07-13 14:50:02 EDT Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2010-07-13 14:50:07 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12879: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:50:07 EDT End: blockcontrol restart
2010-07-13 14:55:07 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14600: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 14:55:08 EDT End: blockcontrol restart
2010-07-13 15:00:08 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18503: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:00:08 EDT End: blockcontrol restart
2010-07-13 15:05:08 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22022: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:05:09 EDT End: blockcontrol restart
2010-07-13 15:10:09 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25009: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:10:09 EDT End: blockcontrol restart
2010-07-13 15:15:09 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28669: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:15:10 EDT End: blockcontrol restart
2010-07-13 15:20:10 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32473: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:20:10 EDT End: blockcontrol restart
2010-07-13 15:25:10 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3222: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:25:11 EDT End: blockcontrol restart
2010-07-13 15:30:11 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6908: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:30:11 EDT End: blockcontrol restart
2010-07-13 15:35:11 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10818: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:35:12 EDT End: blockcontrol restart
2010-07-13 15:40:12 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14585: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:40:12 EDT End: blockcontrol restart
2010-07-13 15:45:12 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 17573: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:45:13 EDT End: blockcontrol restart
2010-07-13 15:50:13 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20679: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:50:13 EDT End: blockcontrol restart
2010-07-13 15:55:13 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24555: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 15:55:14 EDT End: blockcontrol restart
2010-07-13 16:00:14 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28178: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:00:14 EDT End: blockcontrol restart
2010-07-13 16:05:14 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 31097: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:05:15 EDT End: blockcontrol restart
2010-07-13 16:10:15 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2158: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:10:15 EDT End: blockcontrol restart
2010-07-13 16:15:15 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6140: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:15:16 EDT End: blockcontrol restart
2010-07-13 16:20:16 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 9557: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:20:16 EDT End: blockcontrol restart
2010-07-13 16:25:16 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12539: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:25:17 EDT End: blockcontrol restart
2010-07-13 16:30:17 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16190: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:30:17 EDT End: blockcontrol restart
2010-07-13 16:35:17 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20096: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:35:18 EDT End: blockcontrol restart
2010-07-13 16:40:18 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 23708: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:40:18 EDT End: blockcontrol restart
2010-07-13 16:45:18 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27372: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:45:19 EDT End: blockcontrol restart
2010-07-13 16:50:19 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30305: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:50:19 EDT End: blockcontrol restart
2010-07-13 16:55:19 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1152: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 16:55:19 EDT End: blockcontrol restart
2010-07-13 17:00:20 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5249: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:00:20 EDT End: blockcontrol restart
2010-07-13 17:05:20 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8676: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:05:21 EDT End: blockcontrol restart
2010-07-13 17:10:21 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11614: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:10:21 EDT End: blockcontrol restart
2010-07-13 17:15:21 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 15507: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:15:22 EDT End: blockcontrol restart
2010-07-13 17:20:22 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18792: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:20:22 EDT End: blockcontrol restart
2010-07-13 17:25:22 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 21783: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:25:22 EDT End: blockcontrol restart
2010-07-13 17:30:22 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25535: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:30:22 EDT End: blockcontrol restart
2010-07-13 17:35:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28476: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:35:23 EDT End: blockcontrol restart
2010-07-13 17:40:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32209: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:40:23 EDT End: blockcontrol restart
2010-07-13 17:45:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3123: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:45:24 EDT End: blockcontrol restart
2010-07-13 17:50:24 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6190: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:50:24 EDT End: blockcontrol restart
2010-07-13 17:55:25 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10126: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 17:55:25 EDT End: blockcontrol restart
2010-07-13 18:00:25 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13276: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:00:26 EDT End: blockcontrol restart
2010-07-13 18:05:26 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16728: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:05:26 EDT End: blockcontrol restart
2010-07-13 18:10:26 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20362: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:10:27 EDT End: blockcontrol restart
2010-07-13 18:15:27 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 23769: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:15:27 EDT End: blockcontrol restart
2010-07-13 18:20:27 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27316: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:20:28 EDT End: blockcontrol restart
2010-07-13 18:25:28 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30391: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:25:28 EDT End: blockcontrol restart
2010-07-13 18:30:28 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1072: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:30:29 EDT End: blockcontrol restart
2010-07-13 18:35:29 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5071: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:35:30 EDT End: blockcontrol restart
2010-07-13 18:40:30 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8202: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:40:31 EDT End: blockcontrol restart
2010-07-13 18:45:31 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11223: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:45:31 EDT End: blockcontrol restart
2010-07-13 18:50:31 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14960: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:50:32 EDT End: blockcontrol restart
2010-07-13 18:55:32 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18083: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 18:55:32 EDT End: blockcontrol restart
2010-07-13 19:00:33 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 21025: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:00:33 EDT End: blockcontrol restart
2010-07-13 19:05:33 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24986: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:05:34 EDT End: blockcontrol restart
2010-07-13 19:10:34 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28257: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:10:34 EDT End: blockcontrol restart
2010-07-13 19:15:34 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 31208: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:15:34 EDT End: blockcontrol restart
2010-07-13 19:20:35 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2697: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:20:35 EDT End: blockcontrol restart
2010-07-13 19:25:35 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5968: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:25:35 EDT End: blockcontrol restart
2010-07-13 19:30:36 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8940: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:30:36 EDT End: blockcontrol restart
2010-07-13 19:35:36 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12399: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:35:37 EDT End: blockcontrol restart
2010-07-13 19:40:37 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 15455: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:40:37 EDT End: blockcontrol restart
2010-07-13 19:45:37 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18456: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:45:38 EDT End: blockcontrol restart
2010-07-13 19:50:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22394: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:50:38 EDT End: blockcontrol restart
2010-07-13 19:55:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25519: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 19:55:39 EDT End: blockcontrol restart
2010-07-13 20:00:39 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 29376: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:00:39 EDT End: blockcontrol restart
2010-07-13 20:05:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32456: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:05:38 EDT End: blockcontrol restart
2010-07-13 20:10:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3851: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:10:38 EDT End: blockcontrol restart
2010-07-13 20:15:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 7186: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:15:39 EDT End: blockcontrol restart
2010-07-13 20:20:39 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11493: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:20:40 EDT End: blockcontrol restart
2010-07-13 20:25:40 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14601: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:25:40 EDT End: blockcontrol restart
2010-07-13 20:30:40 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 17971: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:30:40 EDT End: blockcontrol restart
2010-07-13 20:35:40 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22007: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:35:41 EDT End: blockcontrol restart
2010-07-13 20:40:41 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25591: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:40:41 EDT End: blockcontrol restart
2010-07-13 20:45:41 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28511: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:45:42 EDT End: blockcontrol restart
2010-07-13 20:50:42 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32051: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:50:42 EDT End: blockcontrol restart
2010-07-13 20:55:43 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3914: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 20:55:43 EDT End: blockcontrol restart
2010-07-13 21:00:43 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6842: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:00:43 EDT End: blockcontrol restart
2010-07-13 21:05:43 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10678: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:05:44 EDT End: blockcontrol restart
2010-07-13 21:10:44 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13838: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:10:44 EDT End: blockcontrol restart
2010-07-13 21:15:44 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 17295: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:15:45 EDT End: blockcontrol restart
2010-07-13 21:20:45 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20812: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:20:45 EDT End: blockcontrol restart
2010-07-13 21:25:45 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 23791: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:25:46 EDT End: blockcontrol restart
2010-07-13 21:30:46 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
iptables v1.4.4: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.4: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
iptables: No chain/target/match by that name.
   ...fail!
 * Don't worry! There occured some errors during the deletion of the iptables 
 * rules. The most common reason for this is that they did not exist, because
 * moblock was not running.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27634: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:30:46 EDT End: blockcontrol restart
2010-07-13 21:35:46 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30977: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:35:47 EDT End: blockcontrol restart
2010-07-13 21:40:47 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2069: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:40:47 EDT End: blockcontrol restart
2010-07-13 21:45:47 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6049: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:45:48 EDT End: blockcontrol restart
2010-07-13 21:50:48 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 9487: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:50:48 EDT End: blockcontrol restart
2010-07-13 21:55:48 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13270: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 21:55:49 EDT End: blockcontrol restart
2010-07-13 22:00:49 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 17123: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:00:49 EDT End: blockcontrol restart
2010-07-13 22:05:49 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20678: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:05:49 EDT End: blockcontrol restart
2010-07-13 22:10:49 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24508: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:10:50 EDT End: blockcontrol restart
2010-07-13 22:15:50 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27919: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:15:50 EDT End: blockcontrol restart
2010-07-13 22:20:50 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30846: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:20:51 EDT End: blockcontrol restart
2010-07-13 22:25:51 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1899: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:25:52 EDT End: blockcontrol restart
2010-07-13 22:30:52 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6140: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:30:52 EDT End: blockcontrol restart
2010-07-13 22:35:53 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 9578: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:35:53 EDT End: blockcontrol restart
2010-07-13 22:40:53 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12593: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:40:53 EDT End: blockcontrol restart
2010-07-13 22:45:53 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16288: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:45:54 EDT End: blockcontrol restart
2010-07-13 22:50:54 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 19698: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:50:54 EDT End: blockcontrol restart
2010-07-13 22:55:54 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 23506: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 22:55:55 EDT End: blockcontrol restart
2010-07-13 23:00:55 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 26469: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:00:55 EDT End: blockcontrol restart
2010-07-13 23:05:55 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 29880: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:05:55 EDT End: blockcontrol restart
2010-07-13 23:10:55 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1118: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:10:56 EDT End: blockcontrol restart
2010-07-13 23:15:56 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4285: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:15:56 EDT End: blockcontrol restart
2010-07-13 23:20:56 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8214: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:20:57 EDT End: blockcontrol restart
2010-07-13 23:25:57 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11218: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:25:57 EDT End: blockcontrol restart
2010-07-13 23:30:57 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14219: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:30:58 EDT End: blockcontrol restart
2010-07-13 23:35:58 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18152: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:35:58 EDT End: blockcontrol restart
2010-07-13 23:40:58 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 21223: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:40:58 EDT End: blockcontrol restart
2010-07-13 23:45:58 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24192: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:45:59 EDT End: blockcontrol restart
2010-07-13 23:50:59 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28096: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:50:59 EDT End: blockcontrol restart
2010-07-13 23:55:59 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 31066: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-13 23:55:59 EDT End: blockcontrol restart
2010-07-14 00:00:59 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1771: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:01:00 EDT End: blockcontrol restart
2010-07-14 00:06:00 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5720: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:06:00 EDT End: blockcontrol restart
2010-07-14 00:11:00 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8734: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:11:00 EDT End: blockcontrol restart
2010-07-14 00:16:00 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11879: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:16:01 EDT End: blockcontrol restart
2010-07-14 00:21:01 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 15357: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:21:01 EDT End: blockcontrol restart
2010-07-14 00:26:01 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18285: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:26:01 EDT End: blockcontrol restart
2010-07-14 00:31:02 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22041: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:31:02 EDT End: blockcontrol restart
2010-07-14 00:36:02 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25059: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:36:02 EDT End: blockcontrol restart
2010-07-14 00:41:02 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28146: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:41:03 EDT End: blockcontrol restart
2010-07-14 00:46:03 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32065: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:46:03 EDT End: blockcontrol restart
2010-07-14 00:51:03 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3645: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:51:04 EDT End: blockcontrol restart
2010-07-14 00:56:04 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6647: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 00:56:04 EDT End: blockcontrol restart
2010-07-14 01:01:04 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 9539: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:01:04 EDT End: blockcontrol restart
2010-07-14 01:06:04 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13265: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:06:05 EDT End: blockcontrol restart
2010-07-14 01:11:05 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16653: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:11:05 EDT End: blockcontrol restart
2010-07-14 01:16:05 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 19573: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:16:05 EDT End: blockcontrol restart
2010-07-14 01:21:05 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22951: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:21:06 EDT End: blockcontrol restart
2010-07-14 01:26:06 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 26445: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:26:06 EDT End: blockcontrol restart
2010-07-14 01:31:06 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 29383: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:31:06 EDT End: blockcontrol restart
2010-07-14 01:36:07 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 530: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:36:07 EDT End: blockcontrol restart
2010-07-14 01:41:07 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4132: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:41:07 EDT End: blockcontrol restart
2010-07-14 01:46:07 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 7288: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:46:08 EDT End: blockcontrol restart
2010-07-14 01:51:08 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11133: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:51:08 EDT End: blockcontrol restart
2010-07-14 01:56:08 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 14511: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 01:56:09 EDT End: blockcontrol restart
2010-07-14 02:01:09 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 18168: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:01:10 EDT End: blockcontrol restart
2010-07-14 02:06:10 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 21181: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:06:10 EDT End: blockcontrol restart
2010-07-14 02:11:10 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 25679: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:11:11 EDT End: blockcontrol restart
2010-07-14 02:16:11 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 29807: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:16:11 EDT End: blockcontrol restart
2010-07-14 02:21:11 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 32748: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:21:12 EDT End: blockcontrol restart
2010-07-14 02:26:12 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4453: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:26:13 EDT End: blockcontrol restart
2010-07-14 02:31:13 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8686: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:31:14 EDT End: blockcontrol restart
2010-07-14 02:36:14 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 11751: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:36:14 EDT End: blockcontrol restart
2010-07-14 02:41:15 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 15297: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:41:15 EDT End: blockcontrol restart
2010-07-14 02:46:15 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 19424: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:46:15 EDT End: blockcontrol restart
2010-07-14 02:51:16 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22410: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:51:17 EDT End: blockcontrol restart
2010-07-14 02:56:18 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 26508: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 02:56:18 EDT End: blockcontrol restart
2010-07-14 03:01:18 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30147: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:01:18 EDT End: blockcontrol restart
2010-07-14 03:06:19 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 693: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:06:19 EDT End: blockcontrol restart
2010-07-14 03:11:19 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4482: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:11:19 EDT End: blockcontrol restart
2010-07-14 03:16:19 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 7481: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:16:20 EDT End: blockcontrol restart
2010-07-14 03:21:20 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10695: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:21:20 EDT End: blockcontrol restart
2010-07-14 03:26:20 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13645: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:26:20 EDT End: blockcontrol restart
2010-07-14 03:31:20 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 17374: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:31:21 EDT End: blockcontrol restart
2010-07-14 03:36:21 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 21063: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:36:21 EDT End: blockcontrol restart
2010-07-14 03:41:21 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24064: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:41:22 EDT End: blockcontrol restart
2010-07-14 03:46:22 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27546: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:46:22 EDT End: blockcontrol restart
2010-07-14 03:51:22 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30688: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:51:23 EDT End: blockcontrol restart
2010-07-14 03:56:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1788: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 03:56:23 EDT End: blockcontrol restart
2010-07-14 04:01:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5320: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:01:23 EDT End: blockcontrol restart
2010-07-14 04:06:23 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8358: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:06:24 EDT End: blockcontrol restart
2010-07-14 04:11:24 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12097: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:11:24 EDT End: blockcontrol restart
2010-07-14 04:16:24 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 15136: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:16:25 EDT End: blockcontrol restart
2010-07-14 04:21:25 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 19271: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:21:25 EDT End: blockcontrol restart
2010-07-14 04:26:25 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 22292: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:26:26 EDT End: blockcontrol restart
2010-07-14 04:31:26 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 26697: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:31:26 EDT End: blockcontrol restart
2010-07-14 04:36:26 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30512: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:36:27 EDT End: blockcontrol restart
2010-07-14 04:41:27 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 2348: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:41:27 EDT End: blockcontrol restart
2010-07-14 04:46:28 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 5877: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:46:28 EDT End: blockcontrol restart
2010-07-14 04:51:28 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 8959: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:51:28 EDT End: blockcontrol restart
2010-07-14 04:56:29 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 12901: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 04:56:29 EDT End: blockcontrol restart
2010-07-14 05:01:29 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16162: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:01:29 EDT End: blockcontrol restart
2010-07-14 05:06:29 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 19938: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:06:30 EDT End: blockcontrol restart
2010-07-14 05:11:30 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 23288: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:11:31 EDT End: blockcontrol restart
2010-07-14 05:16:31 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27051: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:16:32 EDT End: blockcontrol restart
2010-07-14 05:21:32 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 30519: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:21:32 EDT End: blockcontrol restart
2010-07-14 05:26:33 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 1951: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:26:36 EDT End: blockcontrol restart
2010-07-14 05:31:36 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6697: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:31:37 EDT End: blockcontrol restart
2010-07-14 05:36:37 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10369: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:36:37 EDT End: blockcontrol restart
2010-07-14 05:41:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13838: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:41:38 EDT End: blockcontrol restart
2010-07-14 05:46:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16822: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:46:38 EDT End: blockcontrol restart
2010-07-14 05:51:38 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20329: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:51:39 EDT End: blockcontrol restart
2010-07-14 05:56:39 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24090: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 05:56:40 EDT End: blockcontrol restart
2010-07-14 06:01:40 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 27560: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:01:40 EDT End: blockcontrol restart
2010-07-14 06:06:40 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 31844: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:06:41 EDT End: blockcontrol restart
2010-07-14 06:11:41 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3508: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:11:41 EDT End: blockcontrol restart
2010-07-14 06:16:41 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6613: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:16:42 EDT End: blockcontrol restart
2010-07-14 06:21:42 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 10302: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:21:42 EDT End: blockcontrol restart
2010-07-14 06:26:43 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 13601: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:26:43 EDT End: blockcontrol restart
2010-07-14 06:31:43 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 16631: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:31:44 EDT End: blockcontrol restart
2010-07-14 06:36:44 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 20220: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:36:44 EDT End: blockcontrol restart
2010-07-14 06:41:45 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 24446: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:41:45 EDT End: blockcontrol restart
2010-07-14 06:46:45 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 28074: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:46:45 EDT End: blockcontrol restart
2010-07-14 06:51:45 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 31204: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:51:46 EDT End: blockcontrol restart
2010-07-14 06:56:46 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 3036: No such process
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 06:56:46 EDT End: blockcontrol restart
2010-07-14 06:57:21 EDT Begin: blockcontrol update
Updating blocklists ...
Updating atma_atma... done.
Extracting atma_atma, detected gz... done.
Updating Bluetack_ads... . No update available.
Extracting Bluetack_ads, detected gz... done.
Updating Bluetack_badpeers... . No update available.
Extracting Bluetack_badpeers, detected gz... done.
Updating Bluetack_bogon... . No update available.
Extracting Bluetack_bogon, detected gz... done.
Updating Bluetack_dshield... . No update available.
Extracting Bluetack_dshield, detected gz... done.
Updating Bluetack_edu... . No update available.
Extracting Bluetack_edu, detected gz... done.
Updating Bluetack_for-non-lan-computers... . No update available.
Extracting Bluetack_for-non-lan-computers, detected gz... done.
Updating Bluetack_forum-spam... . No update available.
Extracting Bluetack_forum-spam, detected gz... done.
Updating Bluetack_hijacked... . No update available.
Extracting Bluetack_hijacked, detected gz... done.
Updating Bluetack_iana-multicast... . No update available.
Extracting Bluetack_iana-multicast, detected gz... done.
Updating Bluetack_iana-private... . No update available.
Extracting Bluetack_iana-private, detected gz... done.
Updating Bluetack_iana-reserved... . No update available.
Extracting Bluetack_iana-reserved, detected gz... done.
Updating Bluetack_level1... . No update available.
Extracting Bluetack_level1, detected gz... done.
Updating Bluetack_level2... . No update available.
Extracting Bluetack_level2, detected gz... done.
Updating Bluetack_level3... . No update available.
Extracting Bluetack_level3, detected gz... done.
Updating Bluetack_Microsoft... . No update available.
Extracting Bluetack_Microsoft, detected gz... done.
Updating Bluetack_proxy... . No update available.
Extracting Bluetack_proxy, detected gz... done.
Updating Bluetack_rangetest... . No update available.
Extracting Bluetack_rangetest, detected gz... done.
Updating Bluetack_spider... . No update available.
Extracting Bluetack_spider, detected gz... done.
Updating Bluetack_spyware... . No update available.
Extracting Bluetack_spyware, detected gz... done.
Updating Bluetack_web-exploit... . No update available.
Extracting Bluetack_web-exploit, detected gz... done.
Updating Bluetack_webexploit-forumspam... . No update available.
Extracting Bluetack_webexploit-forumspam, detected gz... done.
Updating cidr-report_bogon... done.
Extracting cidr-report_bogon, detected gz... done.
Updating dchubad_faker... done.
Extracting dchubad_faker, detected gz... done.
Updating dchubad_hacker... done.
Extracting dchubad_hacker, detected gz... done.
Updating dchubad_spammer... done.
Extracting dchubad_spammer, detected gz... done.
Updating nexus23_ipfilterx... done.
Extracting nexus23_ipfilterx, detected gz... done.
Updating spamhaus_drop... done.
Extracting spamhaus_drop, detected gz... done.
Updating TBG_Bogon... done.
Extracting TBG_Bogon, detected gz... done.
Updating TBG_Business_ISPs... done.
Extracting TBG_Business_ISPs, detected gz... done.
Updating TBG_Educational_Institutions... . No update available.
Extracting TBG_Educational_Institutions, detected gz... done.
Updating TBG_General_Corporate_Ranges... done.
Extracting TBG_General_Corporate_Ranges, detected gz... done.
Updating TBG_Hijacked... 2010-07-14 07:01:46 EDT Begin: blockcontrol restart
Stopping blockcontrol.wd   ...done.
Deleting iptables ...
   ...done.
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 6242: No such process
   ...done.
Building blocklist...  * /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast is empty!
 * wc -l: 0 /var/spool/blockcontrol/Bluetack_iana-multicast/extracted/Bluetack_iana-multicast
 * Keeping old /var/spool/blockcontrol/Bluetack_iana-multicast/used/Bluetack_iana-multicast.
   ...done.
Inserting iptables ...
Allowing inbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing forwarded LAN traffic for 192.168.1.4 with subnetmask 255.255.255.0   ...done.
Allowing outbound traffic to DNS server 192.168.1.1   ...done.
Allowing forwarded traffic to DNS server 192.168.1.1   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-07-14 07:01:51 EDT End: blockcontrol restart
done.
Extracting TBG_Hijacked, detected gz... done.
Updating TBG_Primary_Threats... done.
Extracting TBG_Primary_Threats, detected gz... done.
Updating TBG_Search_Engines... . No update available.
Extracting TBG_Search_Engines, detected gz... done.
Blocklists updated.
Problematic daemon status: 1
 * moblock is not running
```



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by GrantStoner on 2010-07-14
When you're installing try it without including "atma" and the "custom list", but let it use the other iplists. For some reason when I reinstalled without those two it worked just fine. Atma just doesn't like the initial update for whatever reason.

---

### Post by jre on 2010-07-14
Thanks for pointing me to the solution!

It is the IPFilterX that causes the problems. This list is in ipfilter.dat format (leading zeros in the IP e.g. 001.001.001.001). MoBlock only accepts either p2p format (1.1.1.1) which is used by most lists, or ipfilter.dat format.

Generally it is no good idea to use too many lists. Read their description and then decide whether you really want to use it. IPFilterX is designed as a very slim list in contrast to Bluetack's level1, or TBG's Primary Threats. So I see no point in using those together.

---

### Post by GrantStoner on 2010-07-14
No problem. Glad I had the solution.

---

