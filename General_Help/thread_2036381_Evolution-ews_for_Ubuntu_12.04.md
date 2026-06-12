---
title: "Evolution-ews for Ubuntu 12.04"
date: 2012-08-01
forum: General Help
---

### Post by rtierney on 2012-08-01
Hey guys.

Was wondering if anyone knows of a working evolution-ews for 12.04...
I really don't want to go davmail/thunderbird, and I don't want 11.10 either for it.

Would be much appreciated if someone had some insight!

---

### Post by rtierney on 2012-08-02
Just wanted to update this and let everyone know, that I have found someone who built a deb, and it's working for me.

You can find the deb at [https://docs.google.com/file/d/0B8_p85pxZhZeM0ZmS21PdGRWQVk/edit?pli=1](https://docs.google.com/file/d/0B8_p85pxZhZeM0ZmS21PdGRWQVk/edit?pli=1)

There is only a 64-bit package however.

---

### Post by mlentink on 2012-08-03
Anything about the source? I would be a bit anxious to install something from a source I know nothing about....

---

### Post by cariboo on 2012-08-03
Moved to General Help, as this has nothing to do with Ubuntu application development.

---

### Post by rtierney on 2012-08-03
Sadly, I know nothing about the source.
I had stumbled across it somewhere, and then proceeded to test it, and it worked.

---

### Post by arune on 2012-09-18
Hello
There is a PPA for evolution-ews:
[http://ubuntuforums.org/showthread.php?t=1912819](http://ubuntuforums.org/showthread.php?t=1912819)

Edit:
Just found PPA was only for oneiric. Sorry.

Edit2: 
Here is a script for building evolution-ews yourself:
[http://ubuntuforums.org/showthread.php?t=1976894](http://ubuntuforums.org/showthread.php?t=1976894)

---

### Post by smerten on 2013-06-02
> **arune said:**
> There is a PPA for evolution-ews:
[http://ubuntuforums.org/showthread.php?t=1912819](http://ubuntuforums.org/showthread.php?t=1912819)

Edit:
Just found PPA was only for oneiric. Sorry.


I checked the PPA mentioned above. In fact it seems to be based on the same version of evolution as is contained in precise / 12.04. However, three dependencies in this PPA don't work for precise:

```

evolution-ews : Depends: libebook1.2-12 (>= 3.2.2)
            Depends: libecal1.2-10 (>= 3.2.2)
            Depends: libedataserver1.2-15 (>= 3.2.2)

```

However, precise has these packages - they just have an additional dash in their name:

```

$ dpkg-query --list 'libe*'
ii  libebook-1.2-12                               3.2.3-0ubuntu7
ii  libecal-1.2-10                                3.2.3-0ubuntu7
ii  libedataserver-1.2-15                         3.2.3-0ubuntu7

```

I unpacked the package, corrected the dependendies, rebuilt the package, installed it and it works fine AFAICS. Here is the procedure for amd64 architecture:

[LIST]
[*]Download PPA package from [https://launchpad.net/~phurley/+archive/ppa/+packages](https://launchpad.net/~phurley/+archive/ppa/+packages) by opening the details of the package and click to the build for your architecture. There you find a downloadable .deb package. Download it to some directory. 
[*]Unpack by ```
dpkg-deb --raw-extract evolution-ews_3.2.3-0ppa1_amd64.deb evolution-ews_3.2.3-1ppa1_amd64
``` 
[*]Edit ```
evolution-ews_3.2.3-1ppa1_amd64/DEBIAN/control
``` adding three dashes. The respective line looks like this after editing:```
Depends: libc6 (>= 2.7), libcamel-1.2-29 (>= 3.2), libcamel-1.2-29 (<< 3.3), libebook-1.2-12 (>= 3.2.2), libecal-1.2-10 (>= 3.2.2), libedata-book-1.2-11 (>= 3.2.2), libedata-cal-1.2-13 (>= 3.2.2), libedataserver-1.2-15 (>= 3.2.2), libedataserverui-3.0-1 (>= 3.2.2), libevolution (>= 3.2), libevolution (<< 3.3), libgconf2-4 (>= 2.31.1), libglib2.0-0 (>= 2.28), libgtk-3-0 (>= 3.0.0), libical0 (>= 0.42), libsoup2.4-1 (>= 2.32.2), libsqlite3-0 (>= 3.6.0), libxml2 (>= 2.7.4), evolution (>= 3.2.1), evolution-data-server (>= 3.2.1)
``` 
[*]Repackage by ```
dpkg-deb --build evolution-ews_3.2.3-1ppa1_amd64
``` 
[*]Install by ```
dpkg --install evolution-ews_3.2.3-1ppa1_amd64.deb
``` 
[/LIST]
With this plugin installed I can access my Office 365 account using EWS.

Since evolution-ews seems to be not so great in this version I'm planing to use it only for the calendar. For mail I'm still using IMAP.


HTH
Stefan

---

