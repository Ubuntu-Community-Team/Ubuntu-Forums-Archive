---
title: "easiest way to install real player"
date: 2006-05-13
forum: General Help
---

### Post by 2501 on 2006-05-13
just follow the instructions.....................

----------

1) Download the version of RealPlayer thats prepackaged for Xandros Linux. Its a .deb package that works under Hoary.

[https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2](https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2) 

2) Uncompress the .tar.zp2 file to get realplay_10.0.2-1_i386.deb

3) Open a command line shell and cd into the directory that you saved the deb file, (default is ~/Desktop

4) Use Sudo to install the file: sudo dpkg -i realplay_10.0.2-1_i386.deb



If you have the "kdelibs-data" installed, step 4 will fail due to conflicting files. Whether you want to do this or not, here's a quick workaround which might break things (though judging by the file that is in conflict between both packages, i would say it wont break anything):

4b) sudo dpkg -i --force-overwrite realplay_10.0.2-1_i386.deb

---

