---
title: "Which Firefox should be in Lucid Lynx"
date: 2012-02-08
forum: General Help
---

### Post by utnubuuser on 2012-02-08
Hello,

I added the mozilla stable ppa to my sources some while ago, and have Firefox 10 running on Lucid.

I was under the impression that simply removing the ppa from the sources list, uninstalling firefox, then re-installing would return me to firefox 3.x.x or whichever version is native to Lucid. 

When I try to downgrade Firefox and reinstall however, I end up with FF10.

So which version is normal on Lucid? It should be 3.5 shouldn't it?

Thanks.

---

### Post by HiImTye on 2012-02-08
```
$ apt-cache policy firefox
firefox:
  Installed: 10.0+build1-0ubuntu0.11.10.1
  Candidate: 10.0+build1-0ubuntu0.11.10.1
  Version table:
 *** 10.0+build1-0ubuntu0.11.10.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
        100 /var/lib/dpkg/status
     7.0.1+build1+nobinonly-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages

```edit: oh you're using Lucid..
[http://packages.ubuntu.com/lucid/firefox](http://packages.ubuntu.com/lucid/firefox)
also, it's version 10
```
 Package: firefox (10.0+build1-0ubuntu0.10.04.2)
```

---

### Post by papibe on 2012-02-08
The current version should be 10.0.

It was decided to upgrade to a later version. I thought that was going to happen later in February, but it already happened several days ago (read about it [here]("http://www.omgubuntu.co.uk/2012/01/older-versions-of-ubuntu-to-get-latest-firefox-releases/")).

Regards.

---

### Post by uRock on 2012-02-08
I think they finally stopped releasing security updates for 3.*, which forced an upgrade to the new release pattern. Firefox 10 is the current version.

---

### Post by utnubuuser on 2012-02-08
OK.  Thank You very much...

---

