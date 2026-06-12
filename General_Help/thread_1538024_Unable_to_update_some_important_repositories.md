---
title: "Unable to update some important repositories"
date: 2010-07-24
forum: General Help
---

### Post by seers on 2010-07-24
There is now constantly an alert on my top panel saying that I need to update my repositories. However, when I go to do this (I'm assuming that I'm doing this correctly--by clicking "Check") not all are updated and the alert remains. Here is the error message I receive:

```
Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Any advice would be welcome! For the record, I use 10.04 on an IBM ThinkPad X41.

---

### Post by Theft42 on 2010-07-24
I am having somewhat of the same problem here... Except instead of ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg
I get one for the opera Stable Release.

---

### Post by Theft42 on 2010-07-26
BUMP

Anybody 
I apologize if this has been asked before.. I am still quite a noob at ubuntu :lolflag:

---

### Post by darkblane on 2010-10-24
I expect it's your ISP, mostly likely a DNS or routing issue.
I have the same problem with CDEMU, nautilus-elementary and some other sources. I switched my wireless to my ADSL (I'm in the UK and have both ADSL & Cable) router from my cable one and I could get the updates.

Try switching to another connection if there is one available or look for a http proxy you can use for your sources.

Hope this helps :)

---

