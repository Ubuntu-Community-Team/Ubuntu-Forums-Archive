---
title: "Firefox 13 buggy in Ubuntu 12 - Help!"
date: 2012-07-02
forum: General Help
---

### Post by indigobeach on 2012-07-02
Chromium works great, but Firefox 13 is buggy.  the back button does not work anymore after the last system update (end of June 2012) and also I cannot drag icons to the bookmark bar anymore.  I use those features a lot.  Can anyone help me figure out how to fix that, or perhaps just stick with a stable Firefox PPA?  I don't really want to get the latest update on Firefox, would rather stick with the stable version until bugs worked out. Thanks so much!

---

### Post by dino99 on 2012-07-02
if you already have some ppa installed then purge them

sudo apt-get purge ppa:hisnameUhaveinstalled

otherwise:

sudo dpkg-reconfigure  firefox

---

### Post by sgage on 2012-07-02
> **indigobeach said:**
> Chromium works great, but Firefox 13 is buggy.  the back button does not work anymore after the last system update (end of June 2012) and also I cannot drag icons to the bookmark bar anymore.  I use those features a lot.  Can anyone help me figure out how to fix that, or perhaps just stick with a stable Firefox PPA?  I don't really want to get the latest update on Firefox, would rather stick with the stable version until bugs worked out. Thanks so much!

Everything fine here with Firefox - try out Dino's suggestions...

---

### Post by indigobeach on 2012-07-02
I've never installed any PPA, just had the default settings when I did a clean install of Ubuntu 12.  So I just did the reconfig command in terminal & now the back button works at least! 

But i still can't drag icons to bookmark bar, a minor annoyance but the back button was the biggest thing.  Thanks.

---

