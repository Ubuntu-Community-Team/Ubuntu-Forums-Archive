---
title: "Download Delays in Synaptic"
date: 2010-01-26
forum: General Help
---

### Post by nishant.singh28 on 2010-01-26
Whenever I try to install any new software using package manager, software center or apt-get, it gets stuck at Downloading for almost a minute and then the download starts. No problems with the net connections-a high speed connection to backbone through a firewall. It is a fairly new problem. It occurs even while updating the package repos. What is happening?

---

### Post by ladasky on 2010-01-27
I just ungraded to Karmic and I'm having EXACTLY the same problem.  Only my delays are not confined to a single minute, nor are they confined to Synaptic.  
 
Ubuntu Software Center is also very slow.  Right now I'm trying to download the ATI proprietary video driver.  The progress meter slowed to a crawl about 50% of the way through.  Ten minutes later, it looks like it might finally reach the end.
 
In addition, it appears that any installs I do on Synaptic are not actually resulting in installed software?  Example: I attempted to install PyMol in Synaptic, and when I clicked on the Applications menu item I got nothing.  Then I installed PyMol through Software Center.  After an incredible delay, the installation completed...

---

### Post by raktarok on 2010-01-27
Not sure if this will help but try picking a mirror from here and replace the ubuntu repo in your sources file.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Or just use the **Software Sources** from the menu - it has the option of selecting other mirrors.

Edit: and here's a tip to increase the speed while downloading package files.

[http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html](http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html)

---

### Post by nishant.singh28 on 2010-01-27
```
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch http://ubuntuarchive.hnsdc.com/dists/karmic/Release.gpg  Could not resolve 'ubuntuarchive.hnsdc.com'

W: Failed to fetch http://ubuntuarchive.hnsdc.com/dists/karmic/main/i18n/Translation-en_IN.bz2  Could not resolve 'ubuntuarchive.hnsdc.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Download speed is not an issue. It takes a lot of time to start. After that, it's very fast.

---

### Post by abhilashm86 on 2010-04-15
[http://ubuntuforums.org/showthread.php?p=9125634#post9125634](http://ubuntuforums.org/showthread.php?p=9125634#post9125634)

Even i'm having same problem, is all indians who are trying to access main server [http://ubuntuarchive.hnsdc.com/dists/karmic/main/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/main/binary-i386/Packages.gz) 
getting error??

Is this main server stopped as software-center? When i click on ping test in software sources to determine best server, it shows [http://ubuntuarchive.hnsdc.com/](http://ubuntuarchive.hnsdc.com/) , but i can't download any packages? 
Whats best soultion?

---

### Post by john newbuntu on 2010-04-15
Mine works fine.  Just try a different mirror.

---

### Post by arpanaut on 2010-04-15
Seems to be a server problem:

[http://ubuntuforums.org/showpost.php?p=9125878&postcount=4](http://ubuntuforums.org/showpost.php?p=9125878&postcount=4)

---

### Post by nishant.singh28 on 2010-04-15
Yup!! I'm using the US repo now.

---

