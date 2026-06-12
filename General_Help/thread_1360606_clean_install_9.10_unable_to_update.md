---
title: "clean install 9.10 unable to update"
date: 2009-12-21
forum: General Help
---

### Post by hunterkasy on 2009-12-21
I just got done doing a clean install of Ubuntu 9.10 and now when I go to the update manager, it fails to retrieve any files

this is the log when I tried the sudo apt-get clean and the sudo apt-get update


user@user-desktop:~$ sudo apt-get clean
[sudo] password for user:
user@user-desktop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
99% [Waiting for headers] [Connecting to security.ubuntu.com
(91.189.88.37)]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
49% [Connecting to us.archive.ubuntu.com (91.189.88.30)] [Waiting for
headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
30% [Waiting for headers] [Connecting to security.ubuntu.com
(91.189.88.37)]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
24% [Connecting to us.archive.ubuntu.com (91.189.88.30)] [Waiting for
headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
18% [Waiting for headers] [Connecting to security.ubuntu.com
(91.189.88.37)]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US

---

### Post by hunterkasy on 2009-12-21
Does anyone know what to do?

---

### Post by hunterkasy on 2009-12-21
this is when I try to do a update, and I can access the internet through firefox

Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2)
 Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old
ones used instead.

---

### Post by wilee-nilee on 2009-12-21
You might try refresh in synaptic and if there is no change go to software sources and change the repository.
you might also post the apt/sources.list with.

cat gedit /etc/apt/sources.list

---

### Post by hunterkasy on 2009-12-21
user@homeuser-desktop:~$ cat gedit /etc/apt/sources.list
cat: gedit: No such file or directory
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
user@homeuser-desktop:~$

---

### Post by hunterkasy on 2009-12-21
user@homeuser-desktop:~$ gedit /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by wilee-nilee on 2009-12-21
So besides the apt source list which looks okay did you try any of the other options.

---

### Post by hunterkasy on 2009-12-21
I went to system-admin-synaptic package manager
clicked reload, still get the same errors, went to the settings in the SPM and to repositories, changed download from us server to main server, and clicked reload again, get the same error,  

If this is not what you meant I am sorry, I didn't understand then

---

### Post by hunterkasy on 2009-12-22
please let me know what to do next

---

### Post by wilee-nilee on 2009-12-22
I am not sure of any answer here, if your able to access the net it should be working, you might try software sources-other then let it look for the fastest repo, but it seems that you may have some sort of connection problem.

It does show the CD as off in the apt list just check it in software sources to make sure it is not ticked on.

---

### Post by SecretCode on 2009-12-22
Do you by any chance have a proxy set in Synaptic package manager preferences?

And if not, do you perhaps have a caching proxy (like squid) in your own network, or one provided by your ISP?

---

### Post by hunterkasy on 2009-12-22
This is how my network is set up, My internet connects to my smoothwall hardware firewall, then from the smoothwall it goes to a 5 port hub, then from their it goes out to my 2 computers 1 running win 7, the other one running Ubuntu, both can go on the internet with no problems, below I am listing all services running on my smoothwall


Core services:
Logging server 	running 	1 days
DNS proxy server 	running 	1 days
Kernel logging server 	running 	1 days
CRON server 	running 	1 days
Web server 	running 	1 days
Services:
DHCP server 	running 	1 days
SIP server 	stopped 	
Quality of Service traffic shaping 	running 	
UPNP 	stopped 	
Clam Anti-virus server 	running 	1 days
Web proxy 	running 	1 days
SMART monitor 	running 	1 days
Dansguardian Content Filter 	running 	1 days
Guardian Active Response 	running 	1 days
Secure shell server 	running 	1 days
Intrusion Detection System 	running 	1 days
IM proxy server 	running 	1 days
VPN 	stopped 	
Network time server 	running 	1 days
POP3 proxy server 	running 	1 days

---

### Post by hunterkasy on 2009-12-22
I am listing everything about my smoothwall server just for case it can help, just to let you know their is allot of info

[color=purple]_***Report generated with SmoothInfo for SWE 3 v.2.2:***_[/color]

[info="Smoothwall version"]```
Express 3.0-polar-i386-update5
```[/info][info="Firewall config type"]```
RED-GREEN
```[/info][info="Firewall default security policy"]```
Open
```[/info][info="Outgoing filtering"]```
Traffic originating on GREEN is: Allowed with exceptions.
Traffic originating on PURPLE is: Allowed with exceptions.
Traffic originating on ORANGE is: Allowed with exceptions.

```[/info][info="DNS info"]```
DNS servers for RED:
DNS1: 209.81.96.130
DNS2: 209.81.96.49
DNS servers for GREEN:
DNS1: 192.168.1.100
DNS2: 

```[/info][info="Connection type"]```
LAN
```[/info][info="Memory specs"]```
             total       used       free     shared    buffers     cached
Mem:        248372     245192       3180          0      20172      27800
Swap:       247960          0     247960
Total:      496332     245192     251140
```[/info][info="Conntracks"]```
374
```[/info][info="Loaded modules"]```
Module                  Size  Used by
eepro100               25232  0 
3c59x                  37800  0 
mii                     4480  2 eepro100,3c59x
ip_nat_pptp             4740  0 
ip_conntrack_pptp       8464  1 ip_nat_pptp
ip_nat_ftp              2944  0 
ip_conntrack_ftp        6256  1 ip_nat_ftp
ip_nat_irc              2304  0 
ip_conntrack_irc        5488  1 ip_nat_irc
xt_CONNMARK             2304  73 
xt_MARK                 2560  1 
xt_mac                  2048  0 
xt_length               2048  1 
xt_tcpudp               3328  43 
xt_mark                 1792  1 
ipt_dscp                1664  1 
ipt_ipp2p               7424  2 
xt_connmark             1920  107 
ipt_multiport           2432  50 
xt_state                1920  14 
ipt_TOS                 2176  0 
xt_CLASSIFY             2176  31 
ipt_ACCOUNT            10652  12 
ipt_MASQUERADE          2816  3 
ipt_REDIRECT            1920  9 
ipt_REJECT              4352  3 
ipt_LOG                 5888  50 
iptable_mangle          2432  1 
iptable_nat             6276  1 
ip_nat                 13740  6 ip_nat_pptp,ip_nat_ftp,ip_nat_irc,ipt_MASQUERADE,ipt_REDIRECT,iptabl
e_nat
ip_conntrack           41260  12 ip_nat_pptp,ip_conntrack_pptp,ip_nat_ftp,ip_conntrack_ftp,ip_nat_ir
c,ip_conntrack_irc,xt_CONNMARK,xt_connmark,xt_state,ipt_MASQUERADE,iptable_nat,ip_nat
iptable_filter          2432  1 
ip_tables               9688  3 iptable_mangle,iptable_nat,iptable_filter
x_tables                8964  20 xt_CONNMARK,xt_MARK,xt_mac,xt_length,xt_tcpudp,xt_mark,ipt_dscp,ipt
_ipp2p,xt_connmark,ipt_multiport,xt_state,ipt_TOS,xt_CLASSIFY,ipt_ACCOUNT,ipt_MASQUERADE,ipt_REDIREC
T,ipt_REJECT,ipt_LOG,iptable_nat,ip_tables
sch_htb                14464  2 
sch_sfq                 4992  16 
ppp_async               8192  0 
crc_ccitt               2048  1 ppp_async
ppp_synctty             6912  0 
ppp_generic            21140  2 ppp_async,ppp_synctty
slhc                    5760  1 ppp_generic
nls_cp437               5760  0 
vfat                    9472  0 
msdos                   7296  0 
fat                    40988  2 vfat,msdos
usbhid                 26628  0 
uhci_hcd               27152  0 
ohci_hcd               16516  0 
usbcore               102020  4 usbhid,uhci_hcd,ohci_hcd

```[/info][info="Resource usage snapshot"]```
top - 11:27:36 up 1 day,  8:27,  0 users,  load average: 0.23, 0.07, 0.02
 Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
 Cpu(s):  0.5%us,  0.1%sy,  0.0%ni, 98.8%id,  0.3%wa,  0.1%hi,  0.1%si,  0.0%st
 Mem:    248372k total,   243844k used,     4528k free,    19532k buffers
 Swap:   247960k total,        0k used,   247960k free,    26572k cached
 
   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  1218 root      16   0  3684 1796 1068 S  2.0  0.7   4:01.97 trafficlogger      
     1 root      16   0  1428  504  444 S  0.0  0.2   0:00.24 init               
     2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
     3 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
     4 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
     5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
     7 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
    37 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kapmd              
    61 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
    62 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
    64 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
    63 root      15   0     0    0    0 S  0.0  0.0   0:00.19 kswapd0            
   647 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   742 root      15   0     0    0    0 S  0.0  0.0   0:00.39 kjournald          
   781 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald          
   783 root      15   0     0    0    0 S  0.0  0.0   0:03.57 kjournald          
   896 root      17   0  1476  560  476 S  0.0  0.2   0:03.22 syslogd            
   900 root      16   0  2308 1244  368 S  0.0  0.5   0:01.43 klogd              
   905 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
   937 root      15   0  3356 1836 1148 S  0.0  0.7   0:00.00 smoothd            
   938 root      16   0  3348 1400  716 S  0.0  0.6   0:00.00 smoothd            
  1044 root      15   0  1432  216  164 S  0.0  0.1   0:33.85 dhcpcd             
  1237 root      16   0  1480  564  476 S  0.0  0.2   0:00.03 cron               
  1239 root      16   0  4324 2008 1440 S  0.0  0.8   0:00.01 httpd              
  1243 nobody    16   0  4500 2204 1476 S  0.0  0.9   0:00.03 httpd              
  1244 nobody    15   0  4520 2224 1476 S  0.0  0.9   0:00.07 httpd              
  1245 nobody    16   0  4440 1892 1240 S  0.0  0.8   0:00.00 httpd              
  1246 nobody    16   0  4440 1900 1240 S  0.0  0.8   0:00.00 httpd              
  1248 root      15   0  2592 1352  720 S  0.0  0.5   0:00.02 dhcpd              
  1253 nobody    15   0  1596  512  416 S  0.0  0.2   0:01.00 dnsmasq            
  1259 root      19   0  3480 1012  780 S  0.0  0.4   0:00.05 sshd               
  1263 root      16   0  2884  708  472 S  0.0  0.3   0:00.00 ntpd               
  1264 ntpd      16   0  2884  900  664 S  0.0  0.4   0:00.00 ntpd               
  1275 root      15   0  3836  544  368 S  0.0  0.2   0:00.00 squid              
  1277 squid     15   0 18696  16m 1540 S  0.0  6.8   0:32.16 squid              
  1278 squid     19   0  1388  268  224 S  0.0  0.1   0:00.00 unlinkd            
  1282 squid     16   0  1996  500  444 S  0.0  0.2   0:02.45 diskd-daemon       
  1284 imspecto  16   0  4552 2144 1708 S  0.0  0.9   0:00.01 imspector          
  1285 imspecto  18   0  4136  712  436 S  0.0  0.3   0:00.00 imspector          
  1288 imspecto  17   0  4328  876  488 S  0.0  0.4   0:00.00 imspector          
  1293 imspecto  17   0  4588 1332  872 S  0.0  0.5   0:00.00 imspector          
  1294 snort     15   0 53848  36m 2056 S  0.0 15.2   2:08.82 snort              
  1300 clam      15   0 87036  77m 1072 S  0.0 32.1   0:12.07 clamd              
  1303 clam      16   0 87036  77m 1072 S  0.0 32.1   0:00.02 clamd              
  1304 clam      15   0 87036  77m 1072 S  0.0 32.1   0:00.58 clamd              
  1306 clam      16   0  3612  836  644 S  0.0  0.3   0:00.00 p3scan             
  1565 root      15   0  5676 3924  936 S  0.0  1.6   0:00.18 guardian.pl        
  1575 clam      16   0 25944  22m  624 S  0.0  9.4   0:02.50 dansguardian       
  1576 clam      15   0 25948  22m  660 S  0.0  9.4   0:09.60 dansguardian       
  1577 clam      15   0 28876  25m  424 S  0.0 10.5   0:04.15 dansguardian       
  1597 root      17   0  2724  800  648 S  0.0  0.3   0:00.01 smartd             
  1600 root      16   0  1408  412  356 S  0.0  0.2   0:00.00 agetty             
  1601 root      16   0  1408  412  356 S  0.0  0.2   0:00.00 agetty             
  1602 root      16   0  1408  412  356 S  0.0  0.2   0:00.00 agetty             
  1603 root      16   0  1408  412  356 S  0.0  0.2   0:00.00 agetty             
  1604 root      16   0  1412  416  356 S  0.0  0.2   0:00.00 agetty             
  1605 root      16   0  1412  416  356 S  0.0  0.2   0:00.00 agetty             
  2017 clam      16   0 68844  23m  992 S  0.0  9.8   0:00.41 dansguardian       
  2018 clam      16   0 57404  23m  988 S  0.0  9.8   0:00.30 dansguardian       
  2019 clam      16   0 50904  23m  988 S  0.0  9.7   0:00.24 dansguardian       
  2022 clam      16   0 43624  23m  988 S  0.0  9.7   0:00.22 dansguardian       
  2023 clam      16   0 36864  23m  988 S  0.0  9.6   0:00.09 dansguardian       
  2024 clam      16   0 33744  23m  988 S  0.0  9.6   0:00.06 dansguardian       
  2025 clam      16   0 31404  23m  988 S  0.0  9.6   0:00.05 dansguardian       
  2026 clam      16   0 30624  23m  988 S  0.0  9.6   0:00.05 dansguardian       
  2027 clam      16   0 29324  23m  988 S  0.0  9.6   0:00.05 dansguardian       
  2079 clam      16   0 28284  23m  988 S  0.0  9.6   0:00.03 dansguardian       
  2080 clam      16   0 27764  23m  988 S  0.0  9.6   0:00.03 dansguardian       
  2081 clam      16   0 27504  23m  988 S  0.0  9.6   0:00.01 dansguardian       
  2082 clam      16   0 26724  23m  988 S  0.0  9.6   0:00.00 dansguardian       
  2083 clam      16   0 26464  23m  988 S  0.0  9.6   0:00.00 dansguardian       
  2084 clam      16   0 25944  22m  296 S  0.0  9.3   0:00.00 dansguardian       
 30761 clam      16   0  109m  24m 1144 S  0.0 10.2   0:00.97 dansguardian       
 30762 clam      15   0  114m  24m  992 S  0.0 10.2   0:01.03 dansguardian       
 31825 clam      16   0 98532  24m  992 S  0.0 10.0   0:00.85 dansguardian       
 31826 clam      16   0 25944  22m  296 S  0.0  9.3   0:00.00 dansguardian       
 31827 clam      16   0 25944  22m  296 S  0.0  9.3   0:00.00 dansguardian       
 12222 nobody    16   0  4472 2164 1472 S  0.0  0.9   0:00.04 httpd              
 12223 nobody    16   0  4440 1892 1240 S  0.0  0.8   0:00.00 httpd              
 12576 clam      15   0 87036  77m 1072 S  0.0 32.1   0:00.05 clamd              
 12595 nobody    17   0  4900 3588 1360 S  0.0  1.4   0:00.07 smoothinfo.cgi     
 12600 root      16   0  3356 1388  700 S  0.0  0.6   0:00.00 smoothd            
 12601 root      23   0  5076 3748 1324 S  0.0  1.5   0:00.09 smoothinfo.pl      
 12634 root      19   0  1948  876  676 R  0.0  0.4   0:00.00 top                

```[/info][info="CPU"]```
Intel(R) Pentium(R) 4 CPU 2.80GHz (Freq.: 2793.363 MHz - Cache: 1024 KB)
```[/info][info="Interrupt requests"]```
There seems to be at least one shared IRQ in your system!
 IRQ 9 used by eth1
 IRQ 10 used by eth0, uhci_hcd:usb2	<==
 IRQ 11 used by uhci_hcd:usb1, uhci_hcd:usb3	<==
 IRQ 14 used by ide0
 IRQ 15 used by ide1

```[/info][info="Disk space"]```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              13G  406M   12G   4% /
/dev/hda1              20M  5.7M   14M  31% /boot
/dev/hda3             6.1G   63M  5.7G   2% /var/log
```[/info][info="Ethernet adapters as reported by lspci"]```
 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 34)
 Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```[/info][info="Network settings 1"]> [size=90][b][color=#FF0000] eth0      Link encap:Ethernet  HWaddr 00:50:04:AD:74:25  
          inet addr:[/b][/color][color=#000000]**209.81.123.3**[/color][color=#FF0000]**  Bcast:**[/color][color=#000000]**209.81.123.63**[/color][color=#FF0000]**  Mask:**[/color][color=#000000]**255.255.255.192**[/color][color=#FF0000][b]
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2986522 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2647973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2549104698 (2431.0 Mb)  TX bytes:1405358255 (1340.2 Mb)
          Interrupt:10 Base address:0xf80 

 [/color][/b][b][color=#00BF00] eth1      Link encap:Ethernet  HWaddr 00:11:11:BA:3D:27  
          inet addr:[/b][/color][color=#000000]**192.168.1.100**[/color][color=#00BF00]**  Bcast:**[/color][color=#000000]**192.168.1.255**[/color][color=#00BF00]**  Mask:**[/color][color=#000000]**255.255.255.0**[/color][color=#00BF00][b]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2746498 errors:0 dropped:0 overruns:1 frame:0
          TX packets:2999855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1413167049 (1347.7 Mb)  TX bytes:2574398618 (2455.1 Mb)
          Interrupt:9 

 [/color][/b]**[color=#BF00FF] [/color]****[color=#FFBF00] [/color]**lo        Link encap:Local Loopback  
          inet addr:**[color=#000000]127.0.0.1[/color]**  Mask:**[color=#000000]255.0.0.0[/color]**
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:705916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:555959824 (530.2 Mb)  TX bytes:555959824 (530.2 Mb)

[/size][/info][info="Network settings 2"]> [size=90] CONFIG_TYPE=2

 [color=#FF0000]** DEFAULT_GATEWAY= **[/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 DNS1=8.8.8.8 [/b][/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 DNS2=8.8.4.4 [/b][/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 RED_ADDRESS=0.0.0.0 [/b][/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 RED_BROADCAST=255.255.255.255 [/b][/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 RED_DEV=eth0
 RED_DHCP_HOSTNAME=smoothwall3sp1
 RED_DISPLAYDRIVER=3c59x
 RED_DRIVER=3c59x
 RED_DRIVER_OPTIONS=
 RED_NETADDRESS=0.0.0.0
 RED_NETMASK=0.0.0.0 [/b][/size][size=85]*<not applicable>*[/color][color=#FF0000][b]
 RED_TYPE=DHCP
 [/b][/color]
 [color=#00BF00][b] GREEN_ADDRESS=192.168.1.100
 GREEN_BROADCAST=192.168.1.255
 GREEN_DEV=eth1
 GREEN_DISPLAYDRIVER=eepro100
 GREEN_DRIVER=eepro100
 GREEN_DRIVER_OPTIONS=
 GREEN_NETADDRESS=192.168.1.0
 GREEN_NETMASK=255.255.255.0
 [/b][/color]
 [color=#BF00FF][b] PURPLE_DEV=
 [/b][/color]
 [color=#FFBF00][b] ORANGE_DEV=
 [/b][/color] [/size][/info][info="Live settings - Network settings 2 with actual values"]> [color=#400000][i]Please note that in case of pppoX connections, gateway, netaddress and broadcast may be considered irrelevant.

[/i][/color] [size=90] CONFIG_TYPE=2

 [color=#FF0000][b] DEFAULT_GATEWAY=209.81.123.1
 DNS1=209.81.96.130
 DNS2=209.81.96.49
 RED_ADDRESS=209.81.123.3
 RED_BROADCAST=
 RED_DEV=eth0
 RED_DHCP_HOSTNAME=smoothwall3sp1
 RED_DISPLAYDRIVER=3c59x
 RED_DRIVER=3c59x
 RED_DRIVER_OPTIONS=
 RED_NETADDRESS=0.0.0.0
 RED_NETMASK=
 RED_TYPE=DHCP
 [/b][/color]
 [color=#00BF00][b] GREEN_ADDRESS=192.168.1.100
 GREEN_BROADCAST=192.168.1.255
 GREEN_DEV=eth1
 GREEN_DISPLAYDRIVER=eepro100
 GREEN_DRIVER=eepro100
 GREEN_DRIVER_OPTIONS=
 GREEN_NETADDRESS=192.168.1.0
 GREEN_NETMASK=255.255.255.0
 [/b][/color]
 [color=#BF00FF][b] PURPLE_DEV=
 [/b][/color]
 [color=#FFBF00][b] ORANGE_DEV=
 [/b][/color] [/size][/info][info="Core services status"]```
CRON server (cron): running
DNS proxy server (dnsmasq): running
Web server (httpd): running
Logging server (klogd): running
SetUID Daemon (smoothd): running

```[/info][info="Stock services status"]```
Remote access (SSH server): on
DHCP server on green: on
IM Proxy: on
Pop3 Proxy: on
Web Proxy: on, in transparent mode
IDS (Snort): on

```[/info][info="Mod services status"]```
 Dansguardian Web Content Filter (DGAV): on
 Smoothwall Express Mail Filter (SEMF): off
 Guardian Active Response (GAR): on
 
```[/info][info="Web proxy settings"]```
Standard Web proxy
===========================
Transparent: on
Cache size (MB): 1048
Remote proxy: 
Max object size (KB): 20480
Min object size (KB): 0
Max outgoing size (KB): 0
Max incoming size (KB): 0

```[/info][info="DHCP settings for green"]```
Range of addresses: 192.168.1.5 - 192.168.1.20
Default lease time (mins): 1440
Max lease time (mins): 7200
Primary DNS: 192.168.1.100
Secondary DNS: 
Primary NTP: 
Secondary NTP: 
Primary WINS: 
Secondary WINS: 
Domain name suffix: 
NIS domain: 
Primary NIS: 
Secondary NIS: 

```**Static assignments:**```
tyler-pc,00:12:3F:74:13:01,192.168.1.2,dell,on

```[/info][info="Dhcp leases"]```
IP: 192.168.1.20 Lease started: 2009/12/22 07:14:12 Ends: 2009/12/23 07:14:12 Mac: 00:11:D8:B2:94:A4 Host name: homeuser-desktop

```[/info][info="Routing"]```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.81.123.0    0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         209.81.123.1    0.0.0.0         UG    0      0        0 eth0

```[/info][info="Port forwarding rules"]```
tcp		0.0.0.0/0		6155		192.168.1.2		6155		Enabled		limewire
 udp		0.0.0.0/0		6155		192.168.1.2		6155		Enabled		limewire
 tcp		0.0.0.0/0		50456		192.168.1.2		50456		Enabled		utorrent
 udp		0.0.0.0/0		50456		192.168.1.2		50456		Enabled		utorrent

```[/info][info="3 other detected mods"]```
1 - DGAV-SW3-2.8.0.6-6.4.4.2-i686-b012
2 - GAR-3.0-SWE3
3 - SMART for SWE 3 v.1.3

```[/info]

---

### Post by hunterkasy on 2009-12-22
I also opened up a thread on the smoothwalls forums, hoping that they might bring some light on this.  

[http://community.smoothwall.org/forum/viewtopic.php?f=20&t=33562](http://community.smoothwall.org/forum/viewtopic.php?f=20&t=33562)

---

### Post by hunterkasy on 2009-12-22
does anyone have any more idea's

---

### Post by hunterkasy on 2009-12-22
> **hunterkasy said:**
> does anyone have any more idea's

bump

---

### Post by SecretCode on 2009-12-23
It's  wild thought, but try clearing the web proxy cache in smoothwall. It's possible you might have a bad copy in the cache. However, I run through smoothwall with no problems so there's nothing wrong in principle!

---

### Post by hunterkasy on 2009-12-24
ok, I hooked up a box that has xubuntu 9.10, onto my network ran the update manager ran fine found updates, downloaded the updates just fine, so I know it is not my network setup, nor is it smoothwall, I also ran kubuntu and ubuntu through vmware and had both of them do updates both worked and downloaded just fine. 

then I try that box that has ubuntu 9.10 installed, still fails to connect or receive, (whatever the message was that I have posted earlier.)  I know that box works fine, I had xp pro installed on it before ubuntu

---

### Post by b0nes on 2009-12-31
I'm experiencing the same issues updating as the OP.  Three weeks ago I did a clean install and everything worked perfectly.  I needed the box for another project and wiped it.  Now I've reinstalled from the same media I used previously onto the same computer and updates fail with the errors reported by the OP.

I have Comcast box connected to the Red interface on my vanilla IPCop firewall, dumb 5 port gig-e switch connected to the Green.  I have a pc running XP, a G4 Mac running 10.4, a 2U Dell PE 2550 running Fedora 12, and an XBOX 360 also connected to the switch.  I'm not having network issues with any of the other devices so I'm pretty confident it's not a problem with my network.

lspci shows the NIC as an Intel 82562EZ 10/100.  I ran "dmesg | grep e100" to see if there was a problem loading the driver, eth0 is Up 100Mbps Full Duplex.  I'm not seeing any errors in the syslog or in the messages log.

My problem differs though in that while I can get an ip from my DHCP server and I can connect to the internet the connection speed is unusably slow.  I can't say for sure how slow it is because I can't install any software or load any websites to measure it.  The Network History graph is basically flat-lined with the occasional blip up one pixel.  The graph only goes to 2KiB/s so I'm not sure exactly what one pixel would represent in terms of speed but suffice to say it's really slow.  

Google is not being especially helpful, I tried booting from the cd and had the same problems.  I'm out of ideas and need help please.

---

