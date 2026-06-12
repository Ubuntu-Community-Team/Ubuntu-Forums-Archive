---
title: "Problems installing Xubuntu desktop"
date: 2010-08-29
forum: General Help
---

### Post by rmcellig on 2010-08-29
I am trying to install Xubuntu Desktop on my PC using the Synaptic Package Manager. I am running the latest version of Ubuntu 10.04. I received an error while attempting to install Xubuntu-Desktop and I have a feeling it is repository related. Am I missing a repository? If so, what exactly do I have to do. I am still pretty new to the Ubuntu environment.

Thanks!!!

---

### Post by davidmohammed on 2010-08-29
on your last picture - choose a different server than the default "canada" server.  Hopefully that will help.

---

### Post by rmcellig on 2010-08-29
Thanks!! So far everything is working. I am now in the Xubuntu desktop environment. How can I check if my repositories are working properly. From the screenshots in my last post, are there any other repositories I need to install? If so, is the a command I use in the terminal to get them or can I just use the Synaptic Package Manager?

---

### Post by davidmohammed on 2010-08-30
If you can use update manager and "check" without any errors being displayed then all is fine.

As to additional repositories, "your world is your oyster"...

my favourites on a new installation are to do the following

from a command line

```
sudo apt-get install xubuntu-restricted-extras
```

this will install various codecs, flash, DVD playback etc.

then I would install the m[edibuntu repository]("https://help.ubuntu.com/community/Medibuntu")
There is various stuff on that web-page to install.  My choice would be w32codecs and libdvdcss2

---

### Post by rmcellig on 2010-08-30
Thanks David. As I have mentioned before, I have been a diehard Mac user since 1988. The more I use Ubuntu, the more I love the flexibily and options. I would love to switch over to Ubuntu as my main OS but I have an issue 

I need to somehow resolve. It looks like I need help in setting up a cron job for something I do on my Mac on a weekly basis. On my Mac I use an Application called Audio Hijack Pro that allows me to schedule recordings of my weekly radio shows. I have a radio hooked into my Mac that I use to record my shows. I have been doing this for years now and it works great! I would hav to find a way to do this in Ubuntu and I don't think there is an equivalent app available for Ubuntu so I beleive my only choice is to set up a crontab and have it work in conjunvtion with an audio recording app. If so, I am not clear on how to set this up. Othere than that, Ubuntu is the bomb as far as OS's I have used!! Love it!!

I don't play games so using Ubuntu is not an issue.

---

### Post by rmcellig on 2010-08-30
Sorry for all this code but I seem to be having an error at the very end regarding index files. What should I do?

randy@ubuntumachine:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for randy: 
--2010-08-30 08:13:22--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `[www.medibuntu.org](www.medibuntu.org)'
randy@ubuntumachine:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package app-install-data-medibuntu
randy@ubuntumachine:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-08-30 08:14:52--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-08-30 08:14:58 (13.0 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_CA
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_CA
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages [3,253B]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,867B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Fetched 20.3kB in 36s (561B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
randy@ubuntumachine:~$ clear

randy@ubuntumachine:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-08-30 08:16:22--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[============================================================>] 268         --.-K/s   in 0s      

2010-08-30 08:16:23 (13.1 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_CA
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_CA
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Fetched 10.5kB in 10s (958B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
randy@ubuntumachine:~$

---

### Post by rmcellig on 2010-08-30
I chose the Best server option and now I was able to install the Medibuntu repository withe no problems at all.

What other repositories do you think I should install? 

Where can I locate other repositories that are safe to install and will not harm my machine?

---

### Post by davidmohammed on 2010-08-30
> **rmcellig said:**
> Thanks David. As I have mentioned before, I have been a diehard Mac user since 1988. The more I use Ubuntu, the more I love the flexibily and options. I would love to switch over to Ubuntu as my main OS but I have an issue 

I need to somehow resolve. It looks like I need help in setting up a cron job for something I do on my Mac on a weekly basis. On my Mac I use an Application called Audio Hijack Pro that allows me to schedule recordings of my weekly radio shows. I have a radio hooked into my Mac that I use to record my shows. I have been doing this for years now and it works great! I would hav to find a way to do this in Ubuntu and I don't think there is an equivalent app available for Ubuntu so I beleive my only choice is to set up a crontab and have it work in conjunvtion with an audio recording app. If so, I am not clear on how to set this up. Othere than that, Ubuntu is the bomb as far as OS's I have used!! Love it!!

I don't play games so using Ubuntu is not an issue.

This [link]("http://www.omgubuntu.co.uk/2009/12/record-multiple-radio-stream-at-same.html") may help you with this...

---

### Post by davidmohammed on 2010-08-30
> **rmcellig said:**
> I chose the Best server option and now I was able to install the Medibuntu repository withe no problems at all.

What other repositories do you think I should install? 

Where can I locate other repositories that are safe to install and will not harm my machine?

[Another repository]("http://www.getdeb.net/welcome/") you might like that I use...

---

