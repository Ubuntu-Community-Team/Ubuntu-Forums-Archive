---
title: "Ubuntu 9.10 problems with updates"
date: 2010-01-09
forum: General Help
---

### Post by indrulz on 2010-01-09
Hi Everyone
This is a problems I have had since I've upgraded to 9.10. I have been trying to sort this problem out myself without any success. I have reinstalled the OS 2 times and the problem continous. The problem is when I try to update my computer through update manager, the repositories start downloading and at a point they stop and after a while I get a whole list of websites where it says has failed to fetch and this is what it says

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct


AND THEN THIS BIT

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.


I have noticed that all the repositories download properly except for the ones that have au at the front. 

Any help is hugely appreciated !!


Cheers

---

### Post by HermanAB on 2010-01-09
Hmm, in my experience, most Linux problems are due to updates.

If your system is working properly, then an update cannot make it better.  It will either be the same, or worse.  Think about that a bit.

So, I don't ever update my machines.  I re-install them from scratch every year or three.  Servers only get very specific updates if there is a serious problem with something (E.g. the spamassassin bug from a few weeks ago), which may happen once a year or so.

---

### Post by eklavya_18 on 2010-01-15
I had the same problem, but at last I have** found a solution **(may be by mistake). We will have to update the command line way. At the command line write
sudo apt-get update
Voila! It worked for me.
I don't know if a particular server matters here. Just in case, I had selected the Uzbekistan server in the repositories.
Hope this works for you.

---

### Post by jward3010 on 2010-01-15
> **HermanAB said:**
> Hmm, in my experience, most Linux problems are due to updates.

This is not true, the updates that tend to come down fix often very serious security problems and exploitable bugs. The fixes are rarely obvious, they fix something in the background so they don't always look like much has changed, and in my experience, Linux is GOOD because of updates. It's called progress.

95% of the time I update nothing at all happens, it's problem-LESS, only improvements. I would offer advice to HermanAB to update frequently especially if you use Ubuntu online.

Now to get back to your problem, in regard the "AU" repository, it's quite possibly down, offline i.e. it's not your fault. Go into "Software Sources" in the "Administration" menu and pick a different countries repositories (preferrably close to you), if the failures go then it's just a case of the au repository being offline.

---

