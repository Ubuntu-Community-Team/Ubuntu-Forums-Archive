---
title: "Intrepid Packages.gz out of date?"
date: 2010-11-15
forum: General Help
---

### Post by mithadriel on 2010-11-15
Hi,

Apologies if this is in the wrong place ... 

In the process of creating template caches for a Virtuozzo installation for 8.10 and stumbled across some issues which appear to be related to the information in Packages.gz ([http://old-releases.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/](http://old-releases.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/))

Reading from the Packages.gz is fine, but we're getting 404 errors all over the shot with the information contained in there. I've picked gcc-4.3 as an example.

[root@server ~]# curl -s [http://old-releases.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz) | gunzip -c | grep -E '^Package: gcc-4.3-base|^Filename' | grep -A1 ^Package
Package: gcc-4.3-base
Filename: pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu12_i386.deb

[root@server ~]# curl -LI [http://old-releases.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu12_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu12_i386.deb)
HTTP/1.1 404 Not Found
Date: Mon, 15 Nov 2010 13:21:09 GMT
Server: Apache/2.2.8 (Ubuntu)
Content-Type: text/html; charset=iso-8859-1

Not sure what our next steps are from here really?

Thanks
Johnathan

---

### Post by snowpine on 2010-11-15
All support for the 8.10 release has ended. Should you choose to continue using it (not advisable!) you will be responsible for your own package management.

---

### Post by gmargo on 2010-11-15
I think you've found a problem.  That gcc file should certainly be there under old-releases. Perhaps whoever migrated intrepid to old-releases missed part of the job.  Note the inconclusive evidence of the page [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)  - there is no description field for the intrepid directories.  I don't know how to escalate this though.  Is there a way to file bug reports regarding the repositories?

---

