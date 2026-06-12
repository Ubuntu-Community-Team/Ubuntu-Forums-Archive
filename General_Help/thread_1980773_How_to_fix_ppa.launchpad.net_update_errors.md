---
title: "How to fix ppa.launchpad.net update errors ?"
date: 2012-05-15
forum: General Help
---

### Post by DemogorgonZ on 2012-05-15
Hello this is what i get from update manager :

```
W:Failed to fetch http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```Thiese errors started to be anoying .. Thank you for your time guys..

Regards :KS

---

### Post by DemogorgonZ on 2012-05-15
Fixed it :)

---

### Post by trulynon on 2012-06-21
Trying to install **CPUFreq Indicator** and I've got this errors:

```
W: Failed to fetch http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Anyone has an idea what's going on?

---

### Post by dino99 on 2012-06-21
> **trulynon said:**
> Trying to install **CPUFreq Indicator** and I've got this errors:

Anyone has an idea what's going on?

can you get this url from your browser ?

and why you does not use this package from the ubuntu archive ? (via the package manager, ie synaptic, for example)

---

### Post by trulynon on 2012-06-21
> **dino99 said:**
> can you get this url from your browser ?

and why you does not use this package from the ubuntu archive ? (via the package manager, ie synaptic, for example)

Hi dino99, thanks for your reply. I was trying to do this on both ways (Terminal and Synaptic), same error. Here's a screenshot from the Synaptic manager. I seem like someone has removed those files from launchpad.

[img]http://www4.picturepush.com/photo/a/8544972/800/Anonymous/desktop.png[/img]

---

### Post by oldos2er on 2012-06-21
That PPA doesn't have a precise repo, it only goes up to oneiric. I would remove it from your sources.

---

### Post by trulynon on 2012-06-21
> **oldos2er said:**
> That PPA doesn't have a precise repo, it only goes up to oneiric. I would remove it from your sources.

Ok, I'll see. Then any other/replacement recommendation for cpufreq-indicator? My notebook is quite hot even if I do nothing, I'd like do something with it. I used to have a lower temperature working on Windows. Any suggestions? Thanks guys

Here's are actual temps (just browsing the Forum now)
```
Adapter: Virtual device
temp1:        +48.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +34.0°C  (crit = +128.0°C)
temp4:        +46.0°C  (crit = +128.0°C)
temp5:        +26.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)
```

I'm working on HP Probook 4530s (i3, 320/7200rpm, HD3000, 3GB RAM)

---

### Post by jpash83 on 2012-08-16
DemogorgonZ:

I'm getting the same errors with respect to various PPA on my first install..404 not found/ failed to fetch etc. Wondering what you did to solve your problem. 

Thanks!

---

### Post by adi93 on 2012-08-19
Hi, 
I am using ubuntu 11.04 and my update message doesn't seems to work properly. 
After, I click the 'check' button in the manager, I get an error message.
My error message is this:

[LEFT]  ```
W:Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 173.194.36.9 80],
E:Some index files failed to download. They have been ignored, or old ones used instead.
``` [/LEFT]

Can someone help me with this?

---

