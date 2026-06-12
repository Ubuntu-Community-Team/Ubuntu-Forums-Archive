---
title: "Software Center 4 in ubuntu 10.10"
date: 2011-05-19
forum: General Help
---

### Post by lildigiman on 2011-05-19
Since I had issues with 11.04 on my computer, I've reverted back to 10.10 and I'd still like to have the newly updated Software Center. In synaptic I tried adding natty's repository so I could upgrade the Software Center. That process left me with: > Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release](http://archive.canonical.com/ubuntu/dists/natty/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

So since that option has failed, I'm wondering if anyone here has any other ideas of what I could do.

Thanks in advance!

---

### Post by _0R10N on 2011-05-19
> **lildigiman said:**
> Since I had issues with 11.04 on my computer, I've reverted back to 10.10 and I'd still like to have the newly updated Software Center. In synaptic I tried adding natty's repository so I could upgrade the Software Center. That process left me with: 

So since that option has failed, I'm wondering if anyone here has any other ideas of what I could do.

Thanks in advance!

Could you post the entry in the /etc/apt/sources.list for that source link.

Kind regards!

---

### Post by lildigiman on 2011-05-19
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty main
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty main

That's what it is. If this doesn't work, maybe there is some other way to get the latest version of the software center?

---

### Post by dennis1200 on 2011-06-19
The line should be:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main

Note the "us" at the beginning. Same for source. I looked into this for lucid, but trying to get it installed without having synaptic upgrade or remove about a bazillion other packages has kept me from succeeding so far. It's definitely something I would like to see backported to 10.04 and 10.10, depending on the technical feasibility of such a step.

---

### Post by vanadium on 2011-06-19
Either you upgrade to Ubuntu 11.04, or you use the software center that comes with Ubuntu 10.10. Using a repository from a newer Ubuntu version is unsupported and unlikely to work.

---

