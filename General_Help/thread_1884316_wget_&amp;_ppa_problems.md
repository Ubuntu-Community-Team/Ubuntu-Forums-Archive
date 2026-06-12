---
title: "wget &amp; ppa problems"
date: 2011-11-21
forum: General Help
---

### Post by wreadrav on 2011-11-21
I am trying to install Aptana Studio using this article [www.samclarke.com/2011/11/how-to-install-aptana-studio-3-on-ubuntu-11-10-oneiric/]("http://www.samclarke.com/2011/11/how-to-install-aptana-studio-3-on-ubuntu-11-10-oneiric/")

However, i am not able to add the repo, nor am i able to wget the xulrunner.

There seems to be some problem with my settings as any domain gets resolved to 1.0.0.0

```
sudo add-apt-repository ppa:ferramroberto/java

You are about to add the following PPA to your system:
 LffL Java
 PPA esclusivo per l'ultima versione disponibile di JAVA

PPA for the latest version of JAVA

PPA für die neueste Version von JAVA

PPA para la última versión de JAVA

PPA pour la dernière version de JAVA


by LffL http://www.lffl.org

 More info: https://launchpad.net/~ferramroberto/+archive/java
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.UrsW7gwl0N --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 45GFG45DGFHGFD57GJE656DFG34SDFDFFS343ERW3324
gpg: requesting key 3ERW3324 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```My internet connection was proper, so i thought the keyserver might be down or busy.
So, i tried the next step i.e, getting xulrunner using wget.

```
wget -O xulrunner.deb http://launchpadlibrarian.net/70321863/xulrunner-1.9.2_1.9.2.17%2Bbuild3%2Bnobinonly-0ubuntu1_i386.deb
--2011-11-21 01:02:12--  http://launchpadlibrarian.net/70321863/xulrunner-1.9.2_1.9.2.17%2Bbuild3%2Bnobinonly-0ubuntu1_i386.deb
Resolving launchpadlibrarian.net... 1.0.0.0
Connecting to launchpadlibrarian.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.
```From the error i think there is some faulty settings, as the domains are directly resolved to 1.0.0.0

Please, help resolve this problem.

---

### Post by wreadrav on 2011-11-21
> **fenitra said:**
> I know nothing of linux

okay.  Is there anyone that can help me out?

---

### Post by matt_symes on 2011-11-21
Hi

Maybe a DNS resolution issue.

Can you post the output of (from a terminal)
[FONT=monospace]
[/FONT]```
cat /etc/resolv.conf
```

and 

```
nslookup launchpadlibrarian.net
```

and also
```

nslookup launchpadlibrarian.net 8.8.8.8
```

Kind regards

---

