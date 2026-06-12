---
title: "upgrade to 10.10 missing important repos"
date: 2010-10-14
forum: General Help
---

### Post by _jay_ on 2010-10-14
Earlier this week I tried to upgrade from 10.04 to 10.10 but failed with this error in update manager when downloading packages "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release](http://archive.ubuntu.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)"  Today it let me, but called it a "partial update" which I guess I shouldn't have assumed would have been lacking only non-essentials.

I get the same error when I try to add deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main which isn't in my update manager listing. For some reason "software sources" is no longer in my admin pulldown either. I get random log-outs and some programs, like evolution, are acting flaky.

---

### Post by _jay_ on 2010-10-14
I've also tried switching to 2 other mirrors with the same results. Thanks for reading.

---

### Post by xjesse on 2010-10-14
Your software sources can be opened from Synaptic or simply right click the menu icon on the panel and select Edit Menus and check it off. I would just try again later in the day. :)

---

### Post by _jay_ on 2010-10-14
Via synaptic and RIT's mirror I get this: 
> Failed to fetch [http://mirrors.rit.edu/ubuntu/dists/maverick/Release](http://mirrors.rit.edu/ubuntu/dists/maverick/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release](http://archive.ubuntu.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  main'/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.Alfred State mirror:
> Failed to fetch [http://mirror.alfredstate.edu/ubuntu/dists/maverick/Release](http://mirror.alfredstate.edu/ubuntu/dists/maverick/Release)  Unable to find expected entry  main'/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Is every mirror slammed? I wonder if it would be dangerous to download the alternate ISO and try from there.

---

