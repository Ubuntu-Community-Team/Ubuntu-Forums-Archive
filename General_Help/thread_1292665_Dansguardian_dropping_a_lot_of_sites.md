---
title: "Dansguardian dropping a lot of sites"
date: 2009-10-16
forum: General Help
---

### Post by harvodan on 2009-10-16
Hello people, I have a combination of Dansguardian + firehol + tinyproxy that's being used as a transparent proxy in order to filter out stuff on the net. It's working well enough, except that it's dropping (not blocking, mind you) a lot of sites.

I'll enter the address, then nothing will happen, it'll just not connect to the site. This is of course different from normal filtering in that it's not blocking it based on content.

Here are my firehol.conf, dansguardian.conf and tinyproxy.conf files.

firehol.conf
```
#iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

version 5
transparent_squid 8080 "nobody root"

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner nobody -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner nobody -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 3128
iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 3128



# Accept all client traffic on any interface

interface any world
server cups accept
policy drop
protection strong
client all accept

```

tinyproxy.conf minus comments
```
User nobody
Group root
Port 3128
Timeout 600
DefaultErrorFile "/usr/share/tinyproxy/default.html"
StatFile "/usr/share/tinyproxy/stats.html"
Logfile "/var/log/tinyproxy.log"
LogLevel Info
PidFile "/var/run/tinyproxy/tinyproxy.pid"
MaxClients 100
MinSpareServers 5
MaxSpareServers 20
StartServers 10
MaxRequestsPerChild 0
Allow 127.0.0.1
ViaProxyName "tinyproxy"
ConnectPort 443
ConnectPort 563

```

dansguardian.conf, again, minus comments
```
reportinglevel = 3
languagedir = '/etc/dansguardian/languages'
language = 'ukenglish'
loglevel = 2
logexceptionhits = 2
logfileformat = 1
filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
accessdeniedaddress = 'http://YOURSERVER.YOURDOMAIN/cgi-bin/dansguardian.pl'
nonstandarddelimiter = on
usecustombannedimage = on
custombannedimagefile = '/usr/share/dansguardian/transparent1x1.gif'
filtergroups = 1
filtergroupslist = '/etc/dansguardian/lists/filtergroupslist'
bannediplist = '/etc/dansguardian/lists/bannediplist'
exceptioniplist = '/etc/dansguardian/lists/exceptioniplist'
showweightedfound = on
weightedphrasemode = 2
urlcachenumber = 1000
urlcacheage = 900
scancleancache = on
phrasefiltermode = 2
preservecase = 0
hexdecodecontent = off
forcequicksearch = off
reverseaddresslookups = off
reverseclientiplookups = off
logclienthostnames = off
createlistcachefiles = on
maxuploadsize = -1
maxcontentfiltersize = 256
maxcontentramcachescansize = 2000
maxcontentfilecachescansize = 20000
filecachedir = '/tmp'
deletedownloadedtempfiles = on
initialtrickledelay = 20
trickledelay = 10
downloadmanager = '/etc/dansguardian/downloadmanagers/fancy.conf'
downloadmanager = '/etc/dansguardian/downloadmanagers/default.conf'
contentscannertimeout = 60
contentscanexceptions = off
recheckreplacedurls = off
forwardedfor = off
usexforwardedfor = off
logconnectionhandlingerrors = on
logchildprocesshandling = off
maxchildren = 120
minchildren = 8
minsparechildren = 4
preforkchildren = 6
maxsparechildren = 32
maxagechildren = 500
maxips = 0
ipcfilename = '/tmp/.dguardianipc'
urlipcfilename = '/tmp/.dguardianurlipc'
ipipcfilename = '/tmp/.dguardianipipc'
nodaemon = off
nologger = off
logadblocks = off
loguseragent = off
softrestart = off
mailer = '/usr/sbin/sendmail -t'
```

Any ideas, oh mighty ubuntu folks?
Thanks for any and all help.

Daniel

---

### Post by harvodan on 2009-10-16
It seems there was nothing wrong with my configuration whatsoever. It appears that the very latest version of tinyproxy has a bug in it which causes a lot of sites to just be dropped for some reason. I worked around it by using the Jaunty packages for the aforementioned programs and doing things that way. I am using Karmic 64 bit by the way.

So I guess, problem solved, or worked around, or whatever.

---

