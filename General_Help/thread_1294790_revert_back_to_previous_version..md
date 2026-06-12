---
title: "revert back to previous version."
date: 2009-10-18
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2009-10-18
how easy is it to go back to a prior version.

I haven't made a /home partition, and think that might be a problem, so maybe need to create it with gparted live disk and transfer over.

problem is (and no replies in the correct forum) that in 9.10 apt-get seems to not be working, get errors like
> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]


now I'm loath to try and remove it from my netbook as it is far better regarding battery life, though the wifi is still a little dodgy, (sometimes works for hour(s) with no issues, other times it disconnects seconds after connecting, and endlessly cycles asking for the password but not signing in properly)

but the netbook is only for word-processing, and web browsing. (and maybe at a later point for having a look at photos after I've taken them to see any errors that aren't apparent on the somewhat deceiving screen of my dSLR)

however its limiting what I can do with my main PC, as I'm unable to sort out things like burning dvds because it wont download programs via apt-get install (same for synaptic)

---

### Post by juancarlospaco on 2009-10-18
Use** Main Server** to get Updates.

[http://**gb](http://**gb)**.archive.ubuntu.com/   <----NO
[http://archive.ubuntu.com/](http://archive.ubuntu.com/)   <----YES

---

### Post by mike555 on 2009-10-18
you should back up your documents ,etc. to a USB drive. , then just install the version you want ,(karmic will be out final soon ), then put your documents back.


 if your going to a different version I would not use the same /Home stuff you have now (/home contains hidden preferences for a certain version and might mess things up )

---

### Post by mikewhatever on 2009-10-18
According to the error, apt-get seems to be working fine, but the repository is not. Navigate to System->Admin->Software Sources and try a different server.

---

### Post by PsYcHoTiC_MaDmAn on 2009-10-18
switching to the main server has that fixed thanks. however this was something it did (the upgrade process), as I didn't modify the source.list files at all.

---

### Post by mike555 on 2009-10-18
Good idea next time to do a fresh install .........

---

