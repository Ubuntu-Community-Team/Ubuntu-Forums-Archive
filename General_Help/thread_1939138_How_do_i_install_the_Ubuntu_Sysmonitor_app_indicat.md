---
title: "How do i install the Ubuntu Sysmonitor app indicator?"
date: 2012-03-11
forum: General Help
---

### Post by bbno3 on 2012-03-11
this is the code thing i have to put into the terminal
```
sudo add-apt-repository ppa:alexeftimie/ppa
sudo apt-get update
sudo apt-get install indicator-sysmonito
```

but when i do the second one i get 

```
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

and the third one kinda does the same, any ideas? i got it from [http://www.ubuntugeek.com/indicator-sysmonitor-monitor-your-cpu-and-memory-usage-ppa-installation-instructions-included.html](http://www.ubuntugeek.com/indicator-sysmonitor-monitor-your-cpu-and-memory-usage-ppa-installation-instructions-included.html)

---

### Post by 2F4U on 2012-03-11
If you look at the ppa you will see that it doesn't provide packages for Oneiric:

[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/)

You are probably following an outdated tutorial.

---

### Post by raja.genupula on 2012-03-11
> **bbno3 said:**
> this is the code thing i have to put into the terminal
```
sudo add-apt-repository ppa:alexeftimie/ppa
sudo apt-get update
sudo apt-get install indicator-sysmonito
```

but when i do the second one i get 

```
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

and the third one kinda does the same, any ideas? i got it from [http://www.ubuntugeek.com/indicator-sysmonitor-monitor-your-cpu-and-memory-usage-ppa-installation-instructions-included.html](http://www.ubuntugeek.com/indicator-sysmonitor-monitor-your-cpu-and-memory-usage-ppa-installation-instructions-included.html)


[http://www.omgubuntu.co.uk/tag/indicatorapplets/](http://www.omgubuntu.co.uk/tag/indicatorapplets/) see this

---

