---
title: "Why are my machines trying to contact Canonical?"
date: 2009-07-16
forum: General Help
---

### Post by rodmacpherson on 2009-07-16
I have several Xubuntu 8.04.1 machines set up to get updates through an apt proxy. 
Only the Proxy is allowed onto the net.

The other machines do get all of the updates via the proxy (as proven with TCPdump) but they still try to contact canonical every day. 

They have stats turned off in the synaptic repository settings. 

Any ideas why these machines are trying to connect to these servers:
drescher.canonical.com
leningradskaya.canonical.com
jackass.canonical.com
prat.canonical.com
lithium.canonical.com

...always on port 80.

---

### Post by regala on 2009-07-16
> **rodmacpherson said:**
> I have several Xubuntu 8.04.1 machines set up to get updates through an apt proxy. 
Only the Proxy is allowed onto the net.

The other machines do get all of the updates via the proxy (as proven with TCPdump) but they still try to contact canonical every day. 

They have stats turned off in the synaptic repository settings. 

Any ideas why these machines are trying to connect to these servers:
drescher.canonical.com
leningradskaya.canonical.com
jackass.canonical.com
prat.canonical.com
lithium.canonical.com

...always on port 80.

can you show us the content of /etc/apt/sources.list and of every single file in /etc/apt/sources.list.d/ ?

---

### Post by rodmacpherson on 2009-07-16
Not sure how that's relevant Regala, as I said I'm using a proxy. ...but here they are:


/etc/apt/sources.list
----------------------------------------------------------------------------------------------------
#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
----------------------------------------------------------------------------------------------------


More relevant is:

/etc/apt/apt.conf.d/01proxy
----------------------------------------------------------------------------------------------------
Acquire::http { Proxy "http://192.168.111.219:3142"; };
----------------------------------------------------------------------------------------------------


I do not believe that apt is what is trying to connect. apt does connect via the proxy.
The question is what else connects to canonical?

---

### Post by blazemore on 2009-07-16
I was under the impression you had to change every rnetry in Sources if you have an apt caching proxy... I might be wrong though.

---

### Post by regala on 2009-07-16
> **rodmacpherson said:**
> 
I do not believe that apt is what is trying to connect. apt does connect via the proxy.
The question is what else connects to canonical?



<dream>
I was checking you didn't have any entry using ftp://
the config file you showed just tells apt that, when using http transport, use a proxy with bla setting, but if you had any deb [ftp://,](ftp://,) it won't use it

anyway, don't you have a tcpdump capture that displays this connection attempts, which then could say to what services it actually tries to connect (I mean the remote port) ?
</dream>

---

### Post by regala on 2009-07-16
> **rodmacpherson said:**
> 
I do not believe that apt is what is trying to connect. apt does connect via the proxy.
The question is what else connects to canonical?


what you set up in 01-proxy.conf is not the use of apt-proxy.
it sets up the use of an HTTP proxy when apt tries to access HTTP resources.

to use your proxy you have to at least put a line
deb [http://your_proxy_host](http://your_proxy_host)

in fact, I don't know how it can work without any deb line referring to your proxy in sources.list...

---

### Post by rodmacpherson on 2009-07-17
> **regala said:**
> what you set up in 01-proxy.conf is not the use of apt-proxy.
it sets up the use of an HTTP proxy when apt tries to access HTTP resources.

to use your proxy you have to at least put a line
deb [http://your_proxy_host](http://your_proxy_host)

in fact, I don't know how it can work without any deb line referring to your proxy in sources.list...

Exactly. 01-proxy.conf sets apt to use an http proxy for ALL http:// addresses in sources.list which it does beautifully. However SOMETHING (obviously not apt) is still trying to connect to those canonical servers on port 80. Since the machine has no direct internet connection (firewalled) it doesn't work. I guess I'll have to dig in the logs to look for something erroring out at whatever time these happen. (roughly 9 am yesterday... and apt had run (via proxy) sometime the night before. 

BTW. In case anyone reading this wants to know what proxy I used it was Apt-Cacher-NG ...on another machine at the IP listed in 01-proxy.conf, which does have internet access, and proxys APT requests on behalf of the rest of the machines.

---

### Post by regala on 2009-07-21
> **rodmacpherson said:**
> Exactly. 01-proxy.conf sets apt to use an http proxy for ALL http:// addresses in sources.list which it does beautifully. However SOMETHING (obviously not apt) is still trying to connect to those canonical servers on port 80. Since the machine has no direct internet connection (firewalled) it doesn't work. I guess I'll have to dig in the logs to look for something erroring out at whatever time these happen. (roughly 9 am yesterday... and apt had run (via proxy) sometime the night before. 

BTW. In case anyone reading this wants to know what proxy I used it was Apt-Cacher-NG ...on another machine at the IP listed in 01-proxy.conf, which does have internet access, and proxys APT requests on behalf of the rest of the machines.

ok, I understand it better now :)
but you don't need that much sources lines in your sources.list, all that they do is repeating the same request on and on and on to your proxy :)

---

### Post by rodmacpherson on 2009-07-27
> **regala said:**
> ok, I understand it better now :)
but you don't need that much sources lines in your sources.list, all that they do is repeating the same request on and on and on to your proxy :)
Actually each line is a different type of request or a request to retrieve from a different ubuntu server (read the man for ap-cacher-ng, what server you ask to grab it from makes a difference. Apt-Cacher-NG will grab from the requested server, but just one copy as opposed to one for every machine in the network if you didn't use a proxy.

I have run wireshark over the weekend and the stray un-proxied request to canonical that I was seeing was a wget request for the canonical GPG key. ubuntu-archive-keyring.gpg

Assuming that the keys don't change often I can see why this is not causing any problems that it is being blocked, 

Anyone have any ideas where the wget request for Ubuntu's GPG keys comes from?
I'll probably just create a firewall rule to allow all connections from these machines to ubuntu's servers if the request is for that file, but it would be nice to know where in the scripts this is coming from.

---

### Post by trwww on 2009-07-27
> **rodmacpherson said:**
> Anyone have any ideas where the wget request for Ubuntu's GPG keys comes from?

Grep the system for the url that is being fetched.

---

### Post by rodmacpherson on 2009-12-22
seems I never posted the final status of this. 

The system wgets the GPG keys. wget doesn't use the apt proxy settings. 
I made an exception in our firewall to allow any web request going to any canonical server to retrieve a file ending in .gpg

This solved my problems. Now any server can retrieve it's own gpg keys, but all other web traffic is blocked, and all updates by apt are proxied through my apt-cacher-ng machine, with minimal config changes on the servers.

---

### Post by egalvan on 2009-12-22
> **rodmacpherson said:**
> seems I never posted the final status of this. 

The system wgets the GPG keys. wget doesn't use the apt proxy settings. 
I made an exception in our firewall to allow any web request going to any canonical server to retrieve a file ending in .gpg

.

Excellent work. Apt-Cacher-NG is great.

Can you post that rule that lets the keys through?

Thanks
ErnestG

---

