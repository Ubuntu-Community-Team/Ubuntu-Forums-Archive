---
title: "Problems with Update Manager"
date: 2010-07-23
forum: General Help
---

### Post by redfox1160 on 2010-07-23
When I run the Update Manager or Synaptic, the following error pops up:
```
**[B]Could not download all repository indexes**[/B]

The repository may no longer be available or could not be
contacted because of network problems. If available an older
version of the failed index will be used. Otherwise the
repository will be ignored. Check your network connection
and ensure the repository address in the preferences is 
correct.

[I]Failed to fetch http://ppa.launchpad.net/spring/ppa/ubuntu/
dists/lucid/main/binary-i386/Packages.gz 404  Not Found
Some index files failed to download, they have been ignored, 
or old ones used instead.[/I]
```

There is a red triangle with an exclamation point in it that sits on my top panel. It appears after this error occurs, and will not go away until I restart my system.

I am currently running 10.04.

Thanks for any help!

---

### Post by watupgroupie on 2010-07-23
Try removing your Spring PPA and see what results.

---

### Post by redfox1160 on 2010-07-23
> **watupgroupie said:**
> Try removing your Spring PPA and see what results.

Is that in synaptic?

---

### Post by Frogs Hair on 2010-07-23
PPA is located in software sources , and you can access it via synaptic or the icon on the administration menu . Select the Other Software tab.

---

### Post by redfox1160 on 2010-07-25
I removed "spring-ppa-lucid.list" and "spring-ppa-lucid.list.save" from "/etc/apt/sources.list.d". Now the update manager seems to work. Will removing these files do anything to my system? Thanks.

---

### Post by sundays211 on 2010-07-25
> **redfox1160 said:**
> I removed "spring-ppa-lucid.list" and "spring-ppa-lucid.list.save" from "/etc/apt/sources.list.d". Now the update manager seems to work. Will removing these files do anything to my system? Thanks.
nope, removing these lines will simply mean that those two ppa's are not checked when searching for updates for your packages. the easier way to do this would have been simply goinin into system-administration-software sources, and removing those two under the "other software" tab.

---

### Post by yanom on 2010-07-28
Are those the sources for spring rts? I'm having the same problem and I'm an avid Spring player.

---

### Post by redfox1160 on 2010-07-28
> **yanom said:**
> Are those the sources for spring rts? I'm having the same problem and I'm an avid Spring player.

Probably. I never played it, but I do remember looking for an RTS a while back.

---

