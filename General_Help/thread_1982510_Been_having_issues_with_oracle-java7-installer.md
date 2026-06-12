---
title: "Been having issues with oracle-java7-installer"
date: 2012-05-18
forum: General Help
---

### Post by codysblackbox on 2012-05-18
I tried to use the oracle-java7-installer (eugenesan) on my Ubuntu 12.04 machine and it's been giving me nightmares. Whenever I do updates I'm told that there are errors with this package, so I tried to uninstall it from the terminal with no luck. Now I keep having my computer freeze (mouse still works, I can still use ctrl+alt+f2, but I can't click or use many other keyboard commands, such as ctrl+alt+t to open the terminal) and I think it may be related. I tried to uninstall it from synaptic and remove every trace of it but received this error message--


(Reading database ... 199362 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `cdrom'
dpkg: error processing oracle-java7-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
Downloading...
--2012-05-18 16:23:22--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 24.143.196.48, 24.143.196.18
Connecting to download.oracle.com (download.oracle.com)|24.143.196.48|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-05-18 16:23:22--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.61.6.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.61.6.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-05-18 16:23:22--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|24.143.196.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 2.03M=0.002s

2012-05-18 16:23:23 (2.03 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:







Is there something I'm doing wrong? How can I remove this bad package and what package should I use instead?

---

### Post by jnepywoda on 2012-05-20
I'm having the exact same problem.  I tried to install that package onto a completely fresh install of 12.04 and I can't get it to work.  I can't even remove the package; it's half installed with icons appearing in the main menu but it won't launch the application.

---

### Post by jnepywoda on 2012-05-20
codysblackbox,

I found a way to fix the problem elsewhere on this forum:

1. open a terminal (ctrl + alt + T)
2. type: cd /var/lib/dpkg/info/
3. type sudo rm oracle-java7-installer*
4. open Synaptic Package Manager
5. search for "oracle-java7-installer"
6. right click, "completely remove"
7. apply

I'm going to try to reinstall now...  Hope this helps.

---

### Post by codysblackbox on 2012-05-21
Worked like a charm for me! Thank you so much for the help!

---

