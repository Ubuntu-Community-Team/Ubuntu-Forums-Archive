---
title: "Update Manager Problem"
date: 2010-01-31
forum: General Help
---

### Post by Inhumanity on 2010-01-31
[I]"Your system is up-to-date"
The package information was last updated **24** days ago.
[/I]

I'm having this problem for almost a month. How do I fix this?

```

W: Failed to fetch ftp://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not connect to dl.google.com:21 (64.233.181.91), connection timed out [IP: 64.233.181.91 21]

W: Failed to fetch ftp://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_PH.bz2  Unable to connect to dl.google.com ftp: [IP: 64.233.181.91 21]

W: Failed to fetch ftp://deb.opera.com/opera/dists/sid/Release.gpg  Could not connect to deb.opera.com:21 (195.189.143.183), connection timed out

W: Failed to fetch ftp://deb.opera.com/opera/dists/sid/non-free/i18n/Translation-en_PH.bz2  Unable to connect to deb.opera.com ftp:

W: Failed to fetch ftp://deb.playonlinux.com/dists/karmic/Release.gpg  USER failed, server said: SSL/TLS required on the control channel

W: Failed to fetch ftp://deb.playonlinux.com/dists/karmic/main/i18n/Translation-en_PH.bz2  USER failed, server said: SSL/TLS required on the control channel

W: Failed to fetch ftp://deb.playonlinux.com/dists/karmic/main/binary-i386/Packages.gz  USER failed, server said: SSL/TLS required on the control channel

W: Failed to fetch ftp://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/source/Sources.gz  Unable to fetch file, server said '"/chromium-daily/ppa/ubuntu/dists/karmic/main/source/Sources.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/bisigi/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/source/Sources.gz  Unable to fetch file, server said '"/bisigi/ppa/ubuntu/dists/karmic/main/source/Sources.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/tualatrix/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/source/Sources.gz  Unable to fetch file, server said '"/tualatrix/ppa/ubuntu/dists/karmic/main/source/Sources.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/compiz/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/compiz/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/compiz/ppa/ubuntu/dists/karmic/main/source/Sources.gz  Unable to fetch file, server said '"/compiz/ppa/ubuntu/dists/karmic/main/source/Sources.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/dylanmccall/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/dylanmccall/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/pidgin-developers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Failed to fetch ftp://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Unable to fetch file, server said '"/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz": Is not a file  '

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by kronomia on 2010-01-31
Hello! Try to return the settings of your software sources to default. I mean check the settings there and see if there is anything wrong. If you didn't find anything and the problem persist. Log yourself up to one of the IRC of Ubuntu where you will be able to express your problem live. It is strange indeed. Good Luck :KS

---

### Post by Inhumanity on 2010-01-31
Sweet. I just changed the url from **ftp** back to **http**, and now it works like charm.

---

### Post by kronomia on 2010-01-31
Good to know that, let me know if you faced any new problems.

My Regards,
:KS

---

