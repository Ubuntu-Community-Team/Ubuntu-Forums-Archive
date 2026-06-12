---
title: "live-helper (live-build) does not work in maverick"
date: 2010-10-24
forum: General Help
---

### Post by robkey on 2010-10-24
Hi, I built live debian/ubuntu images successfully in lucid and debian testing. When running live-helper (now named live-build) the following error occurs when accessing a file in my own archive

 Failed to fetch [http://localhost/mydebian/pool/utils/s/syslinux/syslinux_4.02+dfsg-7_i386.deb](http://localhost/mydebian/pool/utils/s/syslinux/syslinux_4.02+dfsg-7_i386.deb)  403  Forbidden [IP: 127.0.0.1 80]

Failed to fetch [http://localhost/mydebian/pool/utils/s/syslinux-common/syslinux-common_4.02+dfsg-7_all.deb](http://localhost/mydebian/pool/utils/s/syslinux-common/syslinux-common_4.02+dfsg-7_all.deb)  403  Forbidden [IP: 127.0.0.1 80]


The files exist and used to work when lucid was installed. I can install these files from this archive. It is just live-helper that cannot install these two files. The Packages.gz file in binary-i386 is updated and there is no problem with the archive. I can successfully install my own custom image from this very same archive.

Any help would be appreciated.
Thanks,
   Rob Key:confused:

---

