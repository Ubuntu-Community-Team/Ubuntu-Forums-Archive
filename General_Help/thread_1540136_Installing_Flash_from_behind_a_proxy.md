---
title: "Installing Flash from behind a proxy"
date: 2010-07-27
forum: General Help
---

### Post by Calash on 2010-07-27
I have been running into an issue for a while now and have finally decided to address it.  The problem is with trying to install flashplugin-installer from my work computer.  It seems to be insisting on trying to connect via port 80 despite the fact that my proxy settings are set to 8080

No other package has this issue and for the life of me I cannot find anybody who has the same problem.  Here is the terminal output of the current attempt

```

Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.3) ...
Downloading...
--2010-07-27 12:18:44--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:19:30--  (try: 2)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:20:17--  (try: 3)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:21:05--  (try: 4)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:21:54--  (try: 5)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:22:44--  (try: 6)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:23:35--  (try: 7)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:24:27--  (try: 8)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:25:20--  (try: 9)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:26:14--  (try:10)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-07-27 12:27:09--  (try:11)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... 

```

That URL is accessible via the web browser, so I am forced to believe this is due to it trying on port 80.

Google has been of no real help to me so far.  Can anybody offer any guidance as to how to resolve this?

---

### Post by khelben1979 on 2010-07-27
In **/etc/apt/sources.list** you have the possibility to change ftp mirror of where your Ubuntu system fetches it's packages from. Emacs is a good editor for editing and searching google for other ftp mirrors I'm sure you'll find one.

If you're unable to find a ftp mirror you can download a .deb package directly from Adobe.com.

---

### Post by Calash on 2010-07-27
No such luck.  I changed all the references to the partner repository to point to the media.mit.edu servers and it still tries that same address.

To me it looks that the package is trying to connect and download the update independent of my source list.

for reference here is my current source.list file

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ lucid main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ lucid universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid universe
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ lucid multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb http://archive.canonical.com/ubuntu lucid partner
#deb-src http://archive.canonical.com/ubuntu lucid partner


deb http://ubuntu.media.mit.edu/ubuntu/ lucid partner
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid partner

deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security multiverse

## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"





deb http://getswiftfox.com/builds/debian unstable non-free

```

The partner repo area is what I just edited.

---

### Post by lovinglinux on 2010-07-27
64bit [http://packages.ubuntu.com/lucid/amd64/flashplugin-installer/download](http://packages.ubuntu.com/lucid/amd64/flashplugin-installer/download)

32bit [http://packages.ubuntu.com/lucid/i386/flashplugin-installer/download](http://packages.ubuntu.com/lucid/i386/flashplugin-installer/download)

---

### Post by Calash on 2010-07-27
> **lovinglinux said:**
> 64bit [http://packages.ubuntu.com/lucid/amd64/flashplugin-installer/download](http://packages.ubuntu.com/lucid/amd64/flashplugin-installer/download)

32bit [http://packages.ubuntu.com/lucid/i386/flashplugin-installer/download](http://packages.ubuntu.com/lucid/i386/flashplugin-installer/download)

No good, but at least it confirms the problem.  The issue is that the deb is trying to download on port 80.  I need it to pass the traffic via port 8080 to get past the proxy.

Reading the postinst file in the deb it has the URL coded into it and appears to use wget.  I just tested wget on a random web page and it is trying port 80, so that would be the source of my issue.

I am checking into wget now to see what could be causing this.  It seems to be ignoring my settings.



Edit: Ok, I found the solution.  Wget was not using the global proxy settings.  I had to edit the /etc/wgetrc file and put in my proxy servers and ports there by hand as well as force it to use the proxy.  Here are the lines


```

# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
https_proxy = http://proxy-server.********.com:8080/
http_proxy = http://proxy-server.********.com:8080/
ftp_proxy = http://proxy-server.********.com:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on

```

Now the deb file installed fine.

Thank you both.  You pushed me in the right direction to figure out the problem :)



Doing some research I found a launchpad bug report on this as well.  
[https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469)

---

### Post by joubertdj on 2010-08-12
This helped me dearly with regard to flash not installing behind a proxy, and not recognizing the global settings ... 

Thanks a mil ...

---

### Post by rogerano on 2010-09-16
Thank you. Had exactly the same issue. Was going insane trying to work out why proxy setting were apparently ineffective.

---

### Post by quinnuendo on 2010-12-21
Another thank you for posting the problem and the solution. I was just going through the same thing. I guess there aren't that many people upgrading behind a proxy :) Let's hope they fix this for later versions.

---

### Post by tigermann on 2011-01-18
It would be great if,
System -> Preferences -> Network Proxy,
propagated the proxy settings to /etc/wgetrc.

---

### Post by Worp8d on 2011-09-13
Thankyou! Been trying to fix this for ages.

---

### Post by minj on 2011-09-20
Genious.

---

