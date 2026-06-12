---
title: "Getting this &quot;failed to download repository info&quot; error"
date: 2012-02-10
forum: General Help
---

### Post by coldjeanz on 2012-02-10
I get this notification in the taskbar at the top that the update information is outdated, so I check for updates in Update Manager.

It returns this:

```
W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I checked the "other software" tab and I can see those are there. Should I disable them or do I need them? I don't exactly know why it's doing this all of a sudden, I did change the battery status icons last week so could that have something to do with it? I really have no idea

---

### Post by plucky on 2012-02-10
> **coldjeanz said:**
> I get this notification in the taskbar at the top that the update information is outdated, so I check for updates in Update Manager.

It returns this:

```
W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I checked the "other software" tab and I can see those are there. Should I disable them or do I need them? I don't exactly know why it's doing this all of a sudden, I did change the battery status icons last week so could that have something to do with it? I really have no idea

The PPA for Oneiric doesn't exist,which is why you are getting the 404 error.

See [Here](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/)

So disable/delete it in Software Sources and you should be good to update.

Good luck

---

### Post by coldjeanz on 2012-02-10
thanks

solved

---

