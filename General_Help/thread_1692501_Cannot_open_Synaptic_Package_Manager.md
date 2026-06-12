---
title: "Cannot open Synaptic Package Manager"
date: 2011-02-21
forum: General Help
---

### Post by savafan on 2011-02-21
I've checked other entries about this, but am having no luck with this particular issue. I cannot open my update manager or package manager. I get the following error:

E: Type 'sudo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

When trying to install a package, I get this error:

Software index is broken
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I've tried all I know how...Any help?

---

### Post by sikander3786 on 2011-02-21
Please post the output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by thefasterblueone on 2011-02-21
Run this in terminal and post the results here.

```
cat /etc/apt/sources.list
```

---

### Post by savafan on 2011-02-21
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid multiverse
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-security restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-security restricted multiverse universe #Added by software-properties
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-security universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-security multiverse
# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

sudo apt-get update

echo "deb [http://repository.mein-neues-blog.de:9000/](http://repository.mein-neues-blog.de:9000/) /" | sudo tee -a /etc/apt/sources.list

---

### Post by sikander3786 on 2011-02-21
Edit your souces.list by,

```
gksudo gedit /etc/apt/sources.list
```

And delete these 2 lines at the end of that file. They are never meant to be there.

```

sudo apt-get update

echo "deb http://repository.mein-neues-blog.de:9000/ /" | sudo tee -a /etc/apt/sources.list
```

Save and close the file and run in Terminal,

```
sudo apt-get update
```

I hope there will be no errors.

---

### Post by savafan on 2011-02-21
This seemed to have helped, but I do get the following at the end of the update & this is something I have seen before::

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Fetched 5,786B in 15s (373B/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/lucid/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


This may be a completely unrelated issue, but maybe some help with this would be valuable also.

Thanks so far...

---

### Post by sikander3786 on 2011-02-21
Are you using your router's address as a DNS server? I would recommend trying Google DNS or OpenDNS if you don't know the DNS server of your ISP. Google one is even better than most ISPs. See Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

### Post by savafan on 2011-02-21
> **sikander3786 said:**
> Are you using your router's address as a DNS server? I would recommend trying Google DNS or OpenDNS if you don't know the DNS server of your ISP. Google one is even better than most ISPs. See Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

I'm not exactly sure what you mean about "DNS server"..This is new to me & I'm not sure how this will change things...Looking into it now & always willing to try something new.

Any additional help or advice would be appreciated.

Thank you sikander3786, I am at least able to get to my Managers now.

---

### Post by sikander3786 on 2011-02-21
> **savafan said:**
> I'm not exactly sure what you mean about "DNS server"..This is new to me & I'm not sure how this will change things...Looking into it now & always willing to try something new.

Any additional help or advice would be appreciated.

Thank you sikander3786, I am at least able to get to my Managers now.
[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

[http://compnetworking.about.com/od/dns_domainnamesystem/f/dns_servers.htm](http://compnetworking.about.com/od/dns_domainnamesystem/f/dns_servers.htm)

Click the link below and see what a DNS does actually.

[http://209.85.175.147](http://209.85.175.147)

---

### Post by savafan on 2011-02-21
> **sikander3786 said:**
> [http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

[http://compnetworking.about.com/od/dns_domainnamesystem/f/dns_servers.htm](http://compnetworking.about.com/od/dns_domainnamesystem/f/dns_servers.htm)

Click the link below and see what a DNS does actually.

[http://209.85.175.147](http://209.85.175.147)

Clicking the link takes me directly to Google.

How could this affect how I'm retrieving updates & get the errors: " No address associated with hostname"??

Just curious, but do also apologize for taking up your time

---

### Post by sikander3786 on 2011-02-21
> Something wicked happened resolving 'archive.linux.duke.edu:http

It doesn't know what happened while resolving those addresses. There was no reply from the destination. Domain-name resolution problem...

---

