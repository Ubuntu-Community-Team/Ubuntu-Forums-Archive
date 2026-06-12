---
title: "Ubuntu Update Check. Servers Down??"
date: 2009-11-21
forum: General Help
---

### Post by Uncle Spellbinder on 2009-11-21
Checking for updates gives me the following...

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by darco on 2009-11-21
something is going on...getting same error messages.



darco

---

### Post by DapperMe17 on 2009-11-21
Same here...give it a little time.

---

### Post by elphaba on 2009-11-21
Though not exactly the same error - similar - I've been having trouble with Update for several weeks. Keep hoping problems will go away.

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

Alice

---

### Post by JPWhite on 2009-11-21
Same here on more than one computer. Have been having the isue for several hours now.

---

### Post by Uncle Spellbinder on 2009-11-21
Working fine for me, now. No issues.

---

### Post by ashlayne on 2009-11-22
I am getting the same error with karmic every time I try to upgrade my packages since I switched to Karmic. 

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/Release.gpg  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.budgetdedicated.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

This is a fresh install of Karmic onto a clean disk, as I was unable to upgrade successfully from Jaunty, so there is nothing left over from a previous install.

I guess... now we sit back and wait? :popcorn:

---

### Post by mcgarry83 on 2009-11-22
I'm having the same problem. Yesterday I was in the middle of updates when I accidentally unplugged my laptop (no battery). Afterwards I was unable to boot because of errors with Grub. After a fresh install today, I am unable to update. Every attempt ends with the same failure to connect to the servers.

---

### Post by Uncle Spellbinder on 2009-11-22
There is obviously an issue with the servers. As I said in another thread, just wait. I waited 3 days before I was able to install anything. 

Why there has been no official word on this from Ubuntu escapes me, though.

---

### Post by vkcaspervk on 2009-11-22
Figured I would add my name to the hat, as I have the same issue. None of my computers can connect. Wife's computer was able to update about 9 hours ago tho...

---

### Post by NoaHall on 2009-11-22
If you want to temporary fix it so you can run update without a problem, do this.

"gksudo gedit /etc/apt/sources.list"

Find the line that has something like - "http://security.ubuntu.com/ubuntu/"
Put a "#" in front of it, save, and now you should be able to update without a problem.
Be sure to remove "#" after a couple of days.

---

### Post by darco on 2009-11-22
> **NoaHall said:**
> If you want to temporary fix it so you can run update without a problem, do this.

"gksudo gedit /etc/apt/sources.list"

Find the line that has something like - "http://security.ubuntu.com/ubuntu/"
Put a "#" in front of it, save, and now you should be able to update without a problem.
Be sure to remove "#" after a couple of days.

I believe security is ok now, its other servers that are not responding. 

```
GPG error: http://ubuntu.cs.uaf.edu karmic Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: http://ubuntu.cs.uaf.edu karmic-updates Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by vkcaspervk on 2009-11-22
Cant install tracert... =P 

Okay I cant ping security.ubuntu.com, but [http://network-tools.com/](http://network-tools.com/) can... 
It might be a route problem... May call my ISP and have them look.

---

### Post by nfn6789 on 2009-11-22
i have not been able to update either. decided to reinstall ubuntu, still wont update.
it just started working

---

### Post by NoaHall on 2009-11-22
> **darco said:**
> I believe security is ok now, its other servers that are not responding. 

```
GPG error: http://ubuntu.cs.uaf.edu karmic Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: http://ubuntu.cs.uaf.edu karmic-updates Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch http://ubuntu.cs.uaf.edu/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
```

It looks like you need to add the GPG key. I have no idea what it is for those repos.

---

### Post by darco on 2009-11-22
Ya you are correct. Strange tho because I chose to download from BEST SERVER so why would it prompt me for a key? I reverted to the MAIN SERVER and the update went smoothly.

thxs
darco

**Edit* just recvd a handful of updates

---

### Post by vkcaspervk on 2009-11-22
Just got off the phone with my ISP, they say there **is a routing issue to security.ubuntu.com and us.archive.ubuntu.com**... They are trying to contact the host that is causing the issue, worse case they will re-route. 

My issue is not being able to access the servers at all. Not a PGP key error. =\ Wish it was as simple.

I can access it via proxy, but my route is dead... =(


I had to change mirrors... they are a bit slower, but it seems to work...

---

