---
title: "PPA Repository problem"
date: 2010-02-15
forum: General Help
---

### Post by jamesisin on 2010-02-15
I am working to add a repository to my 8.10 system.  In fact, I have done so.  Here is my blog post with my instructions:

[http://www.soundunreason.com/InkWell/?p=1367](http://www.soundunreason.com/InkWell/?p=1367)

The trouble is that when I attempt to seek out updates I get an error (404) for a specific file:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz)  404 Not Found

Some index files failed to download, they have been ignored, or old ones used instead.

I have confirmed the file exists at that exact location (I even downloaded the file to my Desktop and confirmed its size against the index page).

What's up with this?

---

### Post by plucky on 2010-02-16
> **jamesisin said:**
> I am working to add a repository to my 8.10 system.  In fact, I have done so.  Here is my blog post with my instructions:

[http://www.soundunreason.com/InkWell/?p=1367](http://www.soundunreason.com/InkWell/?p=1367)

The trouble is that when I attempt to seek out updates I get an error (404) for a specific file:



I have confirmed the file exists at that exact location (I even downloaded the file to my Desktop and confirmed its size against the index page).

What's up with this?

This doesn't work:-

[http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz)

This one works:-

[http://ppa.launchpad.net/do-core/ubuntu/dists/intrepid/main/binary-i386/](http://ppa.launchpad.net/do-core/ubuntu/dists/intrepid/main/binary-i386/)

Notice the extra ppa after do-core.


Good Luck

---

### Post by howefield on 2010-02-16
> **jamesisin said:**
> The trouble is that when I attempt to seek out updates I get an error (404) for a specific file:

The link works if you change "interpid" to intrepid.

This doesn't work
[http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/interpid/main/binary-i386/Packages.gz)

But this does
[http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)

---

### Post by jamesisin on 2010-02-16
That's funny.  I kept checking the URI in the Edit Source dialog.  I never looked at the Distribution field more than glancingly.

Thanks.  Amazing what a fresh pair of eyes can accomplish.

---

### Post by howefield on 2010-02-16
> **jamesisin said:**
> Thanks.  Amazing what a fresh pair of eyes can accomplish.

Evidently :)

Easily done.

---

