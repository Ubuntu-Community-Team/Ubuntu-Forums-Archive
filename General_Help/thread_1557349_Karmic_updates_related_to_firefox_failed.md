---
title: "Karmic: updates related to firefox failed"
date: 2010-08-20
forum: General Help
---

### Post by rawlins02 on 2010-08-20
Just tried to do the requested updates on a machine running Karmic Koala. I see that the web site is up and there are firefox-gnome-support files there in the proper directory. Just not the right ones that update is trying to fetch.  


```

W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.9~hg20100813r34531+nobinonly-0ubuntu1~umd1~karmic_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox/firefox-branding_3.6.9~hg20100813r34531+nobinonly-0ubuntu1~umd1~karmic_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox/firefox_3.6.9~hg20100813r34531+nobinonly-0ubuntu1~umd1~karmic_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-gnome-support_1.9.1.12~hg20100813r27049+nobinonly-0ubuntu1~umd1~karmic_i386.deb
  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.12~hg20100813r27049+nobinonly-0ubuntu1~umd1~karmic_i386.deb
  404  Not Found


```

---

### Post by rawlins02 on 2010-08-20
Issue solved (I hope).  I've purged the ppa repository for mozilla, as described in a thread started yesterday:

[http://ubuntuforums.org/showthread.php?t=1556391](http://ubuntuforums.org/showthread.php?t=1556391)

Apologies for not looking through posts over past couple days first.

---

### Post by rawlins02 on 2010-08-25
Just received another "Could not download error" during update of my machine running Karmic: 

```

Failed to fetch http://ppa.launchpad.net/sevenmachines/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

I see there is no ppa directory off of: 

[http://ppa.launchpad.net/sevenmachines/](http://ppa.launchpad.net/sevenmachines/)

Perhaps this is unrelated to the failed update last week.  That said, I'm wondering if this is going to be an ongoing issue for updates?  Have I done something wrong?  A simple solution?

---

