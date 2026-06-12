---
title: "Synaptic: &quot;Failed to fetch&quot; error"
date: 2010-05-04
forum: General Help
---

### Post by Levviathor on 2010-05-04
Currently running 9.10, upgraded from 9.04.

Whenever I run Reload in Synaptic, it gives me this error:

```
Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 81.171.111.247 80]
Failed to fetch http://ppa.launchpad.net/capitanterrex/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I checked both those links, and they don't exist.  If you change /karmic/ to /jaunty/ it works, so it looks like those two repos just weren't updated for karmic.

I still seem to get updates for everything else just fine.  It's just annoying to have an error message pop up every time.

---

### Post by colorlessprism on 2010-05-04
remastersys runs into this regularly, i add the source to list, update, install and then remove remastersys source. it may not be ideal, but i to get tired of seeing this message

---

### Post by Levviathor on 2010-05-04
As you can see in the sources.list file that I just attached (sorry), neither of those two repositories were added by me.  They appear to be part of the official repos, or else exist in a cryptic system file somewhere.

---

### Post by Elfy on 2010-05-04
I would guess they are both in sources.list.d

```
ls /etc/apt/sources.list.d
```

You can just remove them from there and do a apt-get update

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) to re acquire the wine repo

---

### Post by Levviathor on 2010-05-04
W00ts!

The error is gone, thanks to Forrestpiskie, and I also learned a bit more about APT.  This has been a good day.

Thank you all, and good night.

---

