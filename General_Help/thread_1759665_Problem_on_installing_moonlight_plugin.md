---
title: "Problem on installing moonlight plugin"
date: 2011-05-16
forum: General Help
---

### Post by satimis on 2011-05-16
Hi all,

Ubuntu 11.04 desktop 64bit
Firefox 4.0

Some webpages require installation of Silverlight.  I have moonlight-plugin-mozilla and moonlight-plugin-core installed.

$ apt-cache policy moonlight-plugin-core```

moonlight-plugin-core:
  Installed: 2.3-0ubuntu5
  Candidate: 2.3-0ubuntu5
  Version table:
 *** 2.3-0ubuntu5 0
        500 http://hk.archive.ubuntu.com/ubuntu/ natty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

$ apt-cache policy moonlight-plugin-mozilla```

moonlight-plugin-mozilla:
  Installed: 2.3-0ubuntu5
  Candidate: 2.3-0ubuntu5
  Version table:
 *** 2.3-0ubuntu5 0
        500 http://hk.archive.ubuntu.com/ubuntu/ natty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

also on;
[http://go-mono.com/moonlight/download.aspx](http://go-mono.com/moonlight/download.aspx)
download the plugin.

However it didn't install the plugin after download completed.  Pls help.

TIA

B.R.
satimis

---

### Post by directhex on 2011-05-16
You need to uninstall the packaged version in order to use the version from go-mono.com

---

### Post by satimis on 2011-05-16
> **directhex said:**
> You need to uninstall the packaged version in order to use the version from go-mono.com

Thanks for your advice.

Uninstalling moonlight-plugin-mozilla and moonlight-plugin-core didn't help, problem still remaining.  Actually I installed the version on go-mono.com first.  It didn't work.  Then I added the above 2 packages later.

The strange thing was after downloading the package on go-mono.com it asked "install the package".  Clicking "Install" it popup "Restart" Firefox immdiately.  I suspect whether the package has been properly installed or NOT

B.R.
satimis

---

