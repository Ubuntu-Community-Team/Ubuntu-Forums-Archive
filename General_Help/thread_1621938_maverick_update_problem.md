---
title: "maverick update problem"
date: 2010-11-14
forum: General Help
---

### Post by Kenchinito on 2010-11-14
hello, I've been trying to update my computer for a while now and i get this message

W:Failed to fetch [http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/doctormo/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/doctormo/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

when i try to log into the address from the web browser, but i find no maverick directory. Is anyone else getting this problem?

---

### Post by plucky on 2010-11-16
> **Kenchinito said:**
> hello, I've been trying to update my computer for a while now and i get this message

W:Failed to fetch [http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/doctormo/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/doctormo/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

when i try to log into the address from the web browser, but i find no maverick directory. Is anyone else getting this problem?

You probably need to disable them as sources if they don't exist.

Open Synaptic Package Manager and navigate to **Settings > Repositories** and under the **Other Software** tag you should find those repositories.
Un-tick them and then in Synaptic select **Reload** and see if the same error comes up.

Good luck

---

### Post by Jackson4christ on 2010-11-17
But what if they should exist?

I'm getting this same issue with ppa's that do exist added through the proper CL procedures.  What else could be going wrong here?

Dominus Vobiscum
jackson4Chirst

---

### Post by plucky on 2010-11-18
> **Jackson4christ said:**
> But what if they should exist?

I'm getting this same issue with ppa's that do exist added through the proper CL procedures.  What else could be going wrong here?

Dominus Vobiscum
jackson4Chirst

Then the PPA repository is down so just wait and try again later.

---

### Post by Jackson4christ on 2010-11-19
> **plucky said:**
> Then the PPA repository is down so just wait and try again later.
And if trying again later still dosen't work?

---

### Post by plucky on 2010-11-19
> **Jackson4christ said:**
> And if trying again later still dosen't work?

For example in this thread ```
[http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net//doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz)
``` if you copy that url into the address bar of Firefox it gives you ```
Not Found

The requested URL /doctormo/ubuntu/dists/maverick/main/binary-i386/Packages.gz was not found on this server.
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80
```

If you then delete parts of the url, you will eventually get ```
[http://ppa.launchpad.net/doctormo/ubuntu/dists/](http://ppa.launchpad.net/doctormo/ubuntu/dists/)
``` where you will see that the Maverick distribution doesn't exist.

That is why the original PPA gets the 404 error.

Good Luck

---

### Post by Jackson4christ on 2010-11-20
Ah, cool, thank you.

Dominus Vobiscum
jackson4Christ

---

