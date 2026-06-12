---
title: "Updating to Drapper while having firefox 1.5"
date: 2006-05-08
forum: General Help
---

### Post by Omnios on 2006-05-08
I have a seriso question, im not shue if im going to do a full install or download and do a fresh install of drapper. There is one serios issue pertaining to the fact that I installed Firefox 1.5 as per the wiki instructions. Now do I have to uninstall  this package before doing the upgrade as it did all kinds of fancy stuff with links and where it is installed. My main issue is will it break firefox?

---

### Post by Hoffmann on 2006-05-08
[QUOTE=Omnios]I have a seriso question, im not shue if im going to do a full install or download and do a fresh install of drapper. There is one serios issue pertaining to the fact that I installed Firefox 1.5 as per the wiki instructions. Now do I have to uninstall  this package before doing the upgrade as it did all kinds of fancy stuff with links and where it is installed. My main issue is will it break firefox?[/QUOTE]

Nice question!
I have the same doubt.

---

### Post by aysiu on 2006-05-08
You do not have to uninstall the Mozilla version of Firefox. The worst that could happen is that the upgrade replaces your symlink to /usr/bin/firefox

If that happens, just redo these instructions:
```
rm /usr/bin/firefox.ubuntu
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

---

### Post by nalmeth on 2006-05-09
thanks for the tip there asiyu
I was going to recommend fresh install, as I had heard about a lot of firefox 1.5 + dapper problems.
I have had two completely unsuccessful breezy - dapper upgrades, but perhaps things are better now.

---

