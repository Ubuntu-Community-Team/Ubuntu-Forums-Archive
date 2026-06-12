---
title: "apt default release and origin"
date: 2009-10-26
forum: General Help
---

### Post by slakkie on 2009-10-26
Hello all,

I have a question, in apt.conf one can add the following 
```
APT::Default-Release "version";
```

This allows to mix-and-match packages from various releases.

However, once you use this, PPA's also get a Pin-Priority of 990 for that release.

eg 

```
APT::Default-Release "karmic";

apt-cache policy libnm-glib2
libnm-glib2:
  Installed: 0.8~a~git.20091013t193206.679d548-0ubuntu1
  Candidate: 0.8~a~git.20091016t185227.8d65515-0ubuntu2~nmt1
  Version table:
     0.8~a~git.20091016t185227.8d65515-0ubuntu2~nmt1 0
        990 http://ppa.launchpad.net karmic/main Packages
 *** 0.8~a~git.20091013t193206.679d548-0ubuntu1 0
        990 http://nl.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

# Without APT::Default-Release "karmic";
apt-cache policy libnm-glib2
libnm-glib2:
  Installed: 0.8~a~git.20091013t193206.679d548-0ubuntu1
  Candidate: 0.8~a~git.20091013t193206.679d548-0ubuntu1
  Version table:
     0.8~a~git.20091016t185227.8d65515-0ubuntu2~nmt1 0
        300 http://ppa.launchpad.net karmic/main Packages
 *** 0.8~a~git.20091013t193206.679d548-0ubuntu1 0
        995 http://nl.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

Is it possible to add a default origin for default releases?

I can work around it by not using the default release and just use the preferences file for pinning packages (including my default release).

---

### Post by slakkie on 2009-10-28
no-one?

---

