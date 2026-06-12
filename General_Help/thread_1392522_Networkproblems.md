---
title: "Networkproblems"
date: 2010-01-28
forum: General Help
---

### Post by DeMus on 2010-01-28
Hi,

Just as many of you I also have a slow network connection, which results in a long period of DNS lookup (Resolving host). Once the address has been established it's okay, the transfer speed is high, no problem there.

I see this behaviour with all browsers in my Jaunty installation. Firefox is slow to find the address, Chrome gives me the Resolving host message for several seconds, also Epiphany and opera have these problems.

In Jaunty I am experiencing with virtual machines, I use vmware for that. In a Ubuntu 9.10, Ubuntu 10.04 and in Windows7 virtual installation I do not have these problems. Here all browsers are lightning fast. I click a link, or type an address and in a blink of an eye the page is on screen.

My computer is connected to a switch, which in its turn is connected to a router, which handles DHCP. The router's wan side is connected to a cable modem.
I have tried several possibilities regarding settings in Jaunty and in the router concerning the DHCP and DNS settings, nothing makes any difference. I have read many sites Google gives me on my questions and many of them write to switch of DNS pre-fetching in Chrome. I did that but as I wrote before, it is not only Chrome which has the problem. Other browsers in my Jaunty installation have it. The virtual machines work great in that respect.
Anyone any idea what I have to do to get rid of my problems?

if you need more info just tell me and I will supply it.

---

### Post by DeMus on 2010-01-29
Bump.

Please help to make my life a bit less miserable.

---

### Post by Iowan on 2010-01-29
I gotta respond to such a delicious avatar...
Unfortunately, you've covered most of the debug I'd suggest. You've tried different DNS settings - I presume that means different DNS servers and searches in */etc/resolv.conf*? I dunno if */etc/nsswitch.conf* needs adjustment... have you tried it?

---

### Post by DeMus on 2010-01-30
> **Iowan said:**
> I gotta respond to such a delicious avatar...
Unfortunately, you've covered most of the debug I'd suggest. You've tried different DNS settings - I presume that means different DNS servers and searches in */etc/resolv.conf*? I dunno if */etc/nsswitch.conf* needs adjustment... have you tried it?

Thank you for both giving an answer as well as your comment about my avatar.
I looked in the file you suggested and this is it:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Is this good, is that bad? I have no idea.

btw, the avatar is my youngest daughter, so keep your hands off. :-)

---

### Post by MoRoBoShi on 2010-01-30
Ciao,

your /etc/nsswitch.conf is very similiar to mine..except for this row:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

Only the "wins" parameter is missing.

Have you tried to set the line this way:

hosts:          files dns

?

---

### Post by DeMus on 2010-01-30
> **cutygeeths said:**
> Suggest that it is the bandwidth problem / issue. Perhaps the PCs are all dragging down content like music / video etc at the same time, then it will work slow. Depends on your router though the latest N technology works faster than wireless G for example and can handle a little more. I run an N router and whilst it is faster there is no improvement in signal availability around the house.
=======================
[Internet Marketing California](http://www.stickywebmedia.com)
[Developer](http://www.blogfodder.co.uk)

Sorry, it is not a bandwidth problem. I have a 20mbps line and can use it maximal. Once the connection is there it is lightning fast. My problem is the DNS lookup problem which is extremely slow.
Also I have a wired network and not a wireless one.

---

### Post by DeMus on 2010-01-30
> **MoRoBoShi said:**
> Ciao,

your /etc/nsswitch.conf is very similiar to mine..except for this row:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

Only the "wins" parameter is missing.

Have you tried to set the line this way:

hosts:          files dns

?

Thanks for your answer. The wins parameter could have been added when I added samba, to make connection to other (less fortunate) pc's, still using the other OS.

---

### Post by DeMus on 2010-01-30
I have re-installed Jaunty, including Firefox Minefield 3.7a1pre and the latest Chrome. Until now they are both very fast, meaning something has changed in my installation compared to the previous one.
I still did not install the samba client and server, so it is still possible this causes the original problems I had. Will let you know soon.

---

### Post by MoRoBoShi on 2010-01-30
> **DeMus said:**
> Thanks for your answer. The wins parameter could have been added when I added samba, to make connection to other (less fortunate) pc's, still using the other OS.

I  use samba to share my files over my local net too.. but wins parameter  have not been set in my /etc/nsswitch.conf file .(on 9.10).

Is somenthing changing in your /etc/nsswitch.conf file in the new installation?

---

### Post by efflandt on 2010-01-30
One suggestion I have seen is the **libadns1** package, which allows multiple DNS lookups at the same time without blocking each other.  Not sure how that compares with whatever is the default. But it may be worth trying.

Years ago when I first got DSL, my ISP's nameservers lagged, so I installed bind9 in Linux as a caching nameserver (and to practice with DNS zones for local names/IPs on my LAN).  That cached recently previously accessed names, so I could quickly get them again locally instead of from the internet.  I just use that for backup now because my DSL modem/router (running a variation of FreeBSD) does a good enough job fetching and caching names.

---

### Post by DeMus on 2010-01-30
@efflandt: bind is not running now, it was running in the previous installation. Is it a program which hitchhikes on the installation of another program, because I most certainly did not install it intentionally.

@MoRoBoShi: Now I also do not have wins in the /etc/nsswitch.conf file. But I still did not install Samba yet. So, who knows.

---

### Post by cjazz on 2010-01-31
Could this be related to the infamous IPv6 problem? If so, disabling it, as described [here]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html"), might be an option. Note: There are conflicting viewpoints about disabling.

---

### Post by DeMus on 2010-01-31
I think I have finally found what is causing the DNS lookup delays when trying to find a website.
I was right about one thing, it has to do with Samba. Anyway with the way I configured it. In the new installation I can make it come and make it go away again. Problem is, when that DNS lookup problem is gone, my Samba is not fully functioning.

Please have a look at the following website:
[_Mount Samba shares with utf8 encoding using CIFS_]("http://ubuntuforums.org/showthread.php?t=288534")

When I follow the initial thread to the letter I get the DNS lookup problem. When I correct it, my smb shares will not mount automatically, but at least I can browse with no delay.

I want to have some network shares mounted automatically so I can use them in other programs, like the grsync back-up program. Without the shares mounted I can not address them and thus I can not make a back-up from those shares.
How do I set network shares to mount automatically without getting the problems I had?

Anyone?

---

### Post by rnerwein on 2010-01-31
hi
i don't know if it will help you to figure out wat's going on with your dns.
try using (when samba is activated) on the linix side: nslookup any_host. now you got the ip of your dns server. try traceroute ip_of_the_dns_server
do the same in windows with "tracert" to see if they are using differnt server or are going differnt ways.
if yes. have a look at your configuration files.
ciao

---

### Post by DeMus on 2010-01-31
It is definitely caused by the setup of mounting network shares.
In the file /etc/nsswitch.conf is a line which reads:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```

When I place wins in front of dns:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

The mounted drives are visible in Nautilus ans thus also in programs trying to read from or write to them.
Problem is, Firefox and Google Chrome (didn't test it yet on other browsers) suffer from the long DNS lookup.

I have read several "How to's" on the net and nowhere can I find how to automount the network shares without interfering with the DNS lookup.

Who can help?

---

### Post by DeMus on 2010-02-01
> **DeMus said:**
> It is definitely caused by the setup of mounting network shares.
In the file /etc/nsswitch.conf is a line which reads:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```

When I place wins in front of dns:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

The mounted drives are visible in Nautilus ans thus also in programs trying to read from or write to them.
Problem is, Firefox and Google Chrome (didn't test it yet on other browsers) suffer from the long DNS lookup.

I have read several "How to's" on the net and nowhere can I find how to automount the network shares without interfering with the DNS lookup.

Who can help?

I use different copies of the nsswitch.conf file at the moment. I have one for using the internet and one for auto mounting the network shares. I copy the right one (nsswitch.conf-internet or nsswitch.conf-network to nsswtich.conf) and reboot. Then what I want to do at that moment is possible.
It works but it is far from perfect.

Anyone any idea how to mount network shares without the wins problem?

---

### Post by rnerwein on 2010-02-01
hi
sorry i can't help with the network shares. i think you kwon, that every time you change some configuration you have to inform the demons about the changes. the config files are mostely read only once on startup. but you realy don't know all the services and applications using the configuration. therefor the best is. REBOOT after changing config files (seen this to often in real life)
ciao

---

### Post by MoRoBoShi on 2010-02-04
> **DeMus said:**
> 
@MoRoBoShi: Now I also do not have wins in the /etc/nsswitch.conf file. But I still did not install Samba yet. So, who knows.

Yes..I suspected it..
anyway... now as far as I understand you use  2 different copies of /etc/nsswitch.conf, one for internet browsing and one for sharing files...correct?

this is my copy of /etc/nswitch.conf:

user@verystrangetome:~$ more /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Maybe this should depends on ubuntu distro..? currently I'm using Karmic..

Can you post your /etc/samba/smb.conf?

Here is my config (/etc/samba/smb.conf) in  for sharing everything I want on the my local net..without authentication..

[SuperShare]
comment = SUPERShare
path = /path_to/SUPERShare
public = yes
guest account = nobody
browseable = yes
read only = no
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

And this works for Windows, Linux and MacOSx clients!

Ciao.

---

### Post by DeMus on 2010-02-05
MoRoBoShi, thank you for your post.
You are right, I have 2 different copies of the nsswitch.conf file. One I use so I can browse the net without any delay. It has wins placed only at the end of the line starting with hosts. Wins is colored red here, see below. Since it is at the end of the line I don't expect it to be used.

When I want to auto-mount shares on other computers so I can make a back-up from those shares, I copy my file nsswitch.conf-backup to nsswitch.conf and reboot the computer.
Now I use the line with only the blue version of wins in the hosts line. The red one is not there anymore.


```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Blue"]wins[/COLOR] dns mdns4 [COLOR="Red"]wins[/COLOR]
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

My /etc/samba/smb.conf file looks like this:

```
# Type 1: Local Master and Preferred Master
[global]
workgroup = %WORKGROUP%
netbios name = %NETBIOSNAME%
name resolve order = bcast host lmhosts wins
map to guest = Bad User
local master = yes
preferred master = yes
os level = 65

# Enable usershares
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
server string =

# Enable print serving
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes

[SHARE1]
comment Home folder on %NETBIOSNAME%
path = /home/%USER%/
guest ok = yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes
```

In both cases of the nsswitch.conf file the shares I use in my Ubuntu installation, taken care of by the smb.conf file, function well.

What I need is to find a way to use Samba without it interfering with the dns lookup. The solution I have found and am using now is the closest to perfection I can think of. I now it is stupid to copy a different file and having to reboot, but at least it works.
I just wonder how others do this. I am not the only one who wants to browse the internet without delays and having samba shares mounted to my computer.
So, isn't there anyone who can help me find the right way to do that?
Please.

---

### Post by MoRoBoShi on 2010-02-06
Ciao DeMus,
I've enabled WINS server in samba on my desktop, and I've not found any issue with DNS lookup.

This is what I've done:

In /etc/nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4[COLOR=Red] wins[/COLOR]
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

```

In /etc/samba/smb.conf:
```

[global]
workgroup = WORKGROUP
netbios name = MYSambaNAME
wins support = yes
dns proxy = no
name resolve order =  [COLOR=Red]wins[/COLOR] bcast lmhosts host

```

Then I add as WINS server on my Windows desktop the Karmic machine and I resolved my shares running \\MYSambaNAME

This should be the kind of configuration you are trying to get..
I will let you know if any issue will occur and in the next days i will test it with linux and osX machine.

---

### Post by Admiral_Payne on 2010-02-06
Where is %WORKGROUP% defined?

This is a snippet from my smb.conf:
```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LAN

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

```
What about changing the 'wins support' and 'wins server'?
I see you've got a dutch 20 Mb connection, I'd guess ADSL in that case. So your modem is probably using the 192.168.x.x range.
Therefor, you could also try putting: 'interfaces = 192.168.0.0/16 eth0'..

---

### Post by DeMus on 2010-02-06
I do have a Dutch 20mb connection, although not ADSL but cable. Behind the modem is a router which is also DHCP server in the 192.168.0.x series of IP addresses.
I do use DHCP on my computers, although in the router/DHCP server I gave the computers a static link to a fixed address. (Lease)
Can you tell me what I need to change to make things work? I would be very thankful, this is disturbing me for a long time already and I would like it to end here and now.

---

### Post by Admiral_Payne on 2010-02-06
I'm not sure what your workgroup is called... I used "nis" from your nsswitch.conf, but if you left it on standard I think it's MSHOME.

Also, you'll have to check whether or not you're using eth0 for your (network) connection to the other machines. I presume so :)

If it doesn't work, try playing with the comments on the following settings:
```

   server string = %h server (Samba, Ubuntu)
   wins support = yes
;   wins server = w.x.y.z
;   name resolve order = bcast host lmhosts wins
;   bind interfaces only = yes

```

Here, w.x.y.z might be set to the address of your router. If you're in the 192.168.0.x space, it's probably 192.168.0.1 or 192.168.0.254.

---

### Post by DeMus on 2010-02-06
> **Admiral_Payne said:**
> I'm not sure what your workgroup is called... I used "nis" from your nsswitch.conf, but if you left it on standard I think it's MSHOME.

Also, you'll have to check whether or not you're using eth0 for your (network) connection to the other machines. I presume so :)

If it doesn't work, try playing with the comments on the following settings:
```

   server string = %h server (Samba, Ubuntu)
   wins support = yes
;   wins server = w.x.y.z
;   name resolve order = bcast host lmhosts wins
;   bind interfaces only = yes

```

Here, w.x.y.z might be set to the address of your router. If you're in the 192.168.0.x space, it's probably 192.168.0.1 or 192.168.0.254.

I just found a way to get things working.
In the fstab file, in the /etc folder, I made 3 connections to shared folders on other computers. To address these folders I used this format: //pc-name/foldername /media/sharename ....(options)
Since all my computers have semi-fixed addresses (through a DHCP lease) I changed //pc-name into //192.168.0.x
Now, when I boot my computer, the main one in the network (don't let my wife hear this) the shared folders are mounted automatically and I can start making a back-up.
Also web browsing is still lightning fast, especially when using Google Chrome.

I will use this for a while, maybe look for other ways to do this because there has to be a neater way of doing this. I mean I should be able to use the computer name instead of the IP address.

Thanks for all the help you have given me, I have learned a lot again.

---

### Post by MoRoBoShi on 2010-02-06
> 
Here, w.x.y.z might be set to the address of your router. If you're in the 192.168.0.x space, it's probably 192.168.0.1 or 192.168.0.254.

@Admiral_Payne
A line beginning with ; is ignored in smb.conf file.. and as far as I know you cannot act  in samba as server and client at the same time.

@DeMus
I need clarify some points...

Your main problem is that you're experience a long DNS lookup on the machine running Samba which act as WINS server correct?

If yes, which are your network settings?
 
Do you use network manager? (If yes it manage your /etc/resolv.conf too)

Have you reserved your IP address on the router? (I mean the DHCP server, if yes your reserved IP should be outside the DHCP IP range)

---

### Post by DeMus on 2010-02-06
> **MoRoBoShi said:**
> @Admiral_Payne
A line beginning with ; is ignored in smb.conf file.. and as far as I know you cannot act  in samba as server and client at the same time.
[COLOR="Red"]Look [_here_]("http://ubuntu.swerdna.org/ubulanprimer.html") and find that one computer can act as client and browser at the same time.[/COLOR]

@DeMus
I need clarify some points...

Your main problem is that you're experience a long DNS lookup on the machine running Samba which act as WINS server correct?

If yes, which are your network settings?
 
Do you use network manager? (If yes it manage your /etc/resolv.conf too)

Have you reserved your IP address on the router? (I mean the DHCP server, if yes your reserved IP should be outside the DHCP IP range)
[COLOR="red"]I use DHCP, so the addresses of the computers are in the DHCP range. However, the DHCP server is giving each computer a "semi-fixed" address. This is done by a lease and works like this:
the MAC-address of each network card is connected to an IP-address which is then leased by the computer. This way, each time a computer boots, it receives, through DHCP, the same IP-address as always.

When you read my previous post you see I managed to fix things by not using the pc-name but its IP-address.[/COLOR]

---

### Post by MoRoBoShi on 2010-02-06
> 
[COLOR=Black] When you read my previous post you see I managed to fix things by not using the pc-name but its IP-address.

Thus eliminating the need for WINS server..


[/COLOR]

---

### Post by Admiral_Payne on 2010-02-06
> **DeMus said:**
> 
Since all my computers have semi-fixed addresses (through a DHCP lease) I changed //pc-name into //192.168.0.x
Just to clarify: instead of using the computer names you're using their IP address to connect to them, right?
That should work indeed. It also points out why your earlier config didn't work: your router only allocates the IP addresses and doesn't add a local DNS entry.
Because there's no DNS entry, your main computer isn't able to resolve the address through DNS (but apparently through WINS it doesn't have a problem). I guess when it is connecting through WINS it's doing a network broadcast, while the DNS lookup just goes to the (default) nameserver which is your router (that doesn't recognise the given hostname).

> **MoRoBoShi said:**
> @Admiral_Payne
A line beginning with ; is ignored in smb.conf file.. and as far as I know you cannot act  in samba as server and client at the same time.
Yes, that's why the comment lines are still in there. You have to uncomment one and comment the other ;)
I meant, simply flip the switch between 'wins support' and 'wins server'.


Anyway. Good to hear that it's working, I wonder if it'll be the way you need it :)

---

