---
title: "Software upgrade/install using ftp instead of http"
date: 2011-10-19
forum: General Help
---

### Post by kodiakz on 2011-10-19
Hello,

I am sitting behind a http-proxy which is pretty much the reason why software upgrades and installations via repos fail.
I am using 11.10 but experienced the same problem in older versions. Proxy settings are set and apt.conf contains it. Web, email etc. works fine.

While upgrading or installing software via apt or aptitude most of the package downloads fail. Some get through, I might guess that only 10% are downloaded successfully. So running aptitude many times (>10, depending on the amount of packages and size) does complete the download, but it is really, really annoying.

I know from the administration that ftp is not touched by the proxy. My colleague does use debian with ftp updates fine. Since I am only experience problems behind this http-proxy and nowhere else I claim it for my problem. The administration does not really care about.
I was able to tunnel my internet connection via ssh (and it does fine), but the administration definitely does not like it. 

I was not able to set up ftp-repos instead of http. I do not know where to find them all (main, update, backports, multiverse, ...) The sources pulldown menu just offers me http repos. All sources.list I found on the web are using http, google does not help me. How can I change to ftp repos for all my sources?

Cheers,
Marc

---

### Post by kodiakz on 2011-10-20
Solved it by myself. Solution painful easy. Changed all my http to ftp in /etc/apt/apt.conf.
I did set ftp proxy and hat to remove it, everything fine now.

---

