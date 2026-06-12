---
title: "wine repository error"
date: 2011-03-18
forum: General Help
---

### Post by claire14 on 2011-03-18
hi i got this error after typing this ppa:ubuntu-wine/ppa to add the wine repository's  can anyone tell me if it needs anything else ,

thanku if you can help :) 

i'm on ubuntu 10.10 


W:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppavV/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppavV/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppavV/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppavV/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2011-03-19
To get Medibuntu's gpg key, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

> 
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa)[COLOR="Red"]vV[/COLOR]/ubuntu/dists/maverick/main/binary-amd64/Packages.gz

Remove the letters I've marked in red, "vV", in both URLs.

---

### Post by claire14 on 2011-03-20
> **oldos2er said:**
> To get Medibuntu's gpg key, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```



Remove the letters I've marked in red, "vV", in both URLs.


hi thanku  for helping ,
i typed  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783

and

sudo apt-get install [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)
[sudo] password for claire14: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/maverick/main/binary-amd64](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/maverick/main/binary-amd64)
E: Couldn't find any package by regex 'http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/maverick/main/binary-amd64'


can you help , i get fatal error on safari browser on wine and firefox freezes on wine :confused:

---

### Post by vivek.pandey on 2011-03-20
hi 
why at all do you need to download repos .? its already present in synaptic

---

### Post by oldos2er on 2011-03-20
I wasn't very clear in my answer, sorry for that. Follow the instructions here for adding the ubuntu-mozilla-daily PPA: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Can you also run cat /etc/apt/sources.list and post the output here?

Why are you running Firefox through wine?

---

### Post by claire14 on 2011-03-21
> **neo_aryan said:**
> hi 
why at all do you need to download repos .? its already present in synaptic

the wine site says to add them , i havn't installed wine before and programs on it it keep shutting down

---

### Post by oldos2er on 2011-03-21
claire14, maybe you could share with us what your goal is. Running Windows apps in Linux may not be a good solution; Windows apps run best in Windows. You can check a particular program's feasibility here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
Also please give names for the Windows programs if possible.

---

### Post by claire14 on 2011-03-25
> **oldos2er said:**
> claire14, maybe you could share with us what your goal is. Running Windows apps in Linux may not be a good solution; Windows apps run best in Windows. You can check a particular program's feasibility here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
Also please give names for the Windows programs if possible.

i fixed it , thanku for or help  :)

---

