---
title: "Cannot remove a PPA -- Errors"
date: 2011-03-07
forum: General Help
---

### Post by mjwoolley33 on 2011-03-07
Last night I attempted to install the PulseAudio Equalizer.  It appears that i followed some old instructions, because the repository does not seem to exist.

Segment from sudo apt-get update:
```
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 4,923B in 1s (2,476B/s)
W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Long story sort, I found updated info and downloaded a .deb...installed just fine.  Problem is, I cant update now because apt-get hangs on the 404'ed ppa.

I downloaded a package called ppa-purge which promised to remove and purge my bunk ppa.

```
sudo ppa-purge ppa:psyke83/ppa:
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: psyke83 ppa
Warning:  Could not find package list for PPA: psyke83 ppa

```

I'm stuck.  How do I remove this bunk PPA?  It's blocking my ability to update my software, etc.  Any help would be great.  Also, I'm semi-novice so keep the training wheels on ;)

---

### Post by Habitual on 2011-03-07
Open Package Manager > Settings menu  option > Repositories > Other Software
and nuke it to orbit.

---

### Post by mjwoolley33 on 2011-03-07
Success!  Thank you very much!  I will change this to [solved]

---

### Post by Habitual on 2011-03-07
You are very welcome!

---

