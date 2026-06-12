---
title: "weird connection problem"
date: 2006-03-09
forum: General Help
---

### Post by Logi on 2006-03-09
Installed Ubuntu 5.10 two days ago. At first i didn't have internet connection.  Then i found a solution from some web sites. When i disable ipv6 at Firefox (from about:config) i can connect internet with Firefox. But i still can't use "apt-get" command and can't log in my MSN etc. what can i do :confused: 

by the way, sorry for my english.

---

### Post by zAo on 2006-03-09
Did you try [this wiki?]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29")

---

### Post by Logi on 2006-03-09
yes, i tried. didn't work.

---

### Post by jxwest on 2006-03-10
Did you have any luck with this? I have exactly the same problem.

---

### Post by Logi on 2006-03-10
I added some DNS, now i can run apt-get update, apt-get upgrade and apt-get dist-upgrade commands and can log in to MSN.
But i can't use "apt-get install ..." command. Packages don't found, all packages so i can't install any program. I've updated "sources.list" file.

:confused:

---

### Post by MerZo on 2006-03-10
Have you added the repositories for the programs you are trying to install? Multiverse, Universe etc.

---

