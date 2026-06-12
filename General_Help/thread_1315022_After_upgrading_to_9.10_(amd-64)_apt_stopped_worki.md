---
title: "After upgrading to 9.10 (amd-64) apt stopped working"
date: 2009-11-04
forum: General Help
---

### Post by mschonaker on 2009-11-04
Hi, guys

after upgrading to ubuntu 9.10 apt-get update produces this problem, that I'm unable to solve:

  Something wicked happened resolving 'security.ubuntu.com:http' (-11)
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11)
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-11)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I've tried editing sources.list. But that produces the same output.

Anyone with the same problem?

Thanks.

---

### Post by soapBAR2 on 2009-11-04
> [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages

Is that the contents of your sources.list? If so, it seems deformed. Everything after the address should be separated by spaces, not / and -s. Try replacing it with

> [http://security.ubuntu.com](http://security.ubuntu.com) karmic security main

It's either that or your GPG keys are messed up, but even then, you should be getting key errors and not this strange error.

---

### Post by mschonaker on 2009-11-04
Thanks for your answer.

Here's the sources.list that produced the error.

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe restricted multiverse

I've tried more variants with the exact same result.

I've also tried to fetch the gpg files like this:

mschonaker@cuco:~$ wget -q -O- [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg) | apt-key add -

Having the output:
gpg: no valid OpenPGP data found.

I've also tried editing /etc/resolv.conf in many different ways, restarting networking, but nothing seems to work. Same result.

Everything related with networking besides apt-get works normally, including ping, wget (that gets that gpg file as expected), firefox, etc, etc.

Regards.

---

### Post by Laykun on 2009-11-04
I too am getting this error. But my system has been on karmic for over a week now without a problem. Everything else but apt seems to work fine and can resolve names without issue.

---

### Post by mschonaker on 2009-11-05
It's good to know that I'm not alone.

I would love to know what does "Something wicked happened resolving 'archive.ubuntu.com:http' (-11)" mean... :S

---

### Post by limaxray on 2009-11-08
I'm seeing the same error after upgrading from Jaunty.  I have found that if I replace the hostnames in my sources.list file with an IP, apt-get seems to work fine.  

I also am getting this odd error when I try to ssh using a hostname (but again works fine with an IP):

$ ssh limaxray
 ssh: Could not resolve hostname limaxray: Success

Even weirder is I can successfully ping the same hostnames that fail with ssh and apt-get.  Also note, my hosts file hasn't changed and has worked fine in Jaunty for quite sometime.

Just for reference, my nsswitch.conf:

```
passwd:         compat
group:          compat
shadow:         compat

hosts:          wins files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

Any ideas?

---

### Post by mschonaker on 2009-11-08
Thanks, limaxray

That was a great step forward. However now apt-get update results in another different error:

Ign [http://91.189.88.40](http://91.189.88.40) karmic Release.gpg
Ign [http://91.189.88.40](http://91.189.88.40) karmic/main Translation-en_US
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security Release.gpg
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/main Translation-en_US
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/universe Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic/universe Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic/multiverse Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic/restricted Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates Release.gpg
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/main Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/universe Translation-en_US
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/multiverse Translation-en_US
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/restricted Translation-en_US
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security Release
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/multiverse Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/restricted Translation-en_US
Ign [http://91.189.88.40](http://91.189.88.40) karmic Release
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/main Packages/DiffIndex
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates Release 
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/universe Packages/DiffIndex
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/multiverse Packages/DiffIndex
Ign [http://91.189.88.37](http://91.189.88.37) karmic-security/restricted Packages/DiffIndex
Ign [http://91.189.88.40](http://91.189.88.40) karmic/main Packages   
Ign [http://91.189.88.40](http://91.189.88.40) karmic/universe Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic/multiverse Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic/restricted Packages
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security/main Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/main Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/universe Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/multiverse Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/restricted Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic/main Packages   
Ign [http://91.189.88.40](http://91.189.88.40) karmic/universe Packages
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security/universe Packages
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security/multiverse Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic/multiverse Packages
Hit [http://91.189.88.37](http://91.189.88.37) karmic-security/restricted Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic/restricted Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/main Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/universe Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/multiverse Packages
Ign [http://91.189.88.40](http://91.189.88.40) karmic-updates/restricted Packages
Err [http://91.189.88.40](http://91.189.88.40) karmic/main Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic/universe Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic/multiverse Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic/restricted Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic-updates/main Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic-updates/universe Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic-updates/multiverse Packages
  301 Moved Permanently
Err [http://91.189.88.40](http://91.189.88.40) karmic-updates/restricted Packages
  301 Moved Permanently
W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic/main/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic/main/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic/universe/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic/universe/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic/multiverse/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic/multiverse/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic/restricted/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic/restricted/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic-updates/main/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic-updates/main/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages)  301 Moved Permanently

W: Failed to fetch [http://91.189.88.40/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages](http://91.189.88.40/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages)  301 Moved Permanently

E: Some index files failed to download, they have been ignored, or old ones used instead.


It seems it's not adding ".gz" at the end of the URLs. Those URLs don't exist in the server.

Any clue?

Regards.

---

### Post by Laykun on 2009-11-08
> **limaxray said:**
> I'm seeing the same error after upgrading from Jaunty.  I have found that if I replace the hostnames in my sources.list file with an IP, apt-get seems to work fine.  

I also am getting this odd error when I try to ssh using a hostname (but again works fine with an IP):

$ ssh limaxray
 ssh: Could not resolve hostname limaxray: Success



Ah, excellent, this fixed the problem for me too. But it seems like somewhat or an inconvenience. I'm hoping that after a few updates this issue will be resolved, and I can go back to using host names.

---

### Post by ngaupakyip on 2009-11-14
I think there is a conflict with winbind.  I had the same problem on my system after installing winbind.  The problem vanished when I uninstalled winbind (and removed "wins" from the "hosts" line in nsswitch.conf).

I'm a newbie with bug issues.  If someone can confirm the winbind conflict, how then should it be reported?

---

