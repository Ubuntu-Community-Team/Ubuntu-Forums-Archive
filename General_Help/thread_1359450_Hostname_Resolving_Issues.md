---
title: "Hostname Resolving Issues"
date: 2009-12-19
forum: General Help
---

### Post by rapfnny on 2009-12-19
Hello there. I'm having a small issue on one my Ubuntu 8.10 Server Edition servers. For example, butternothingsdfsdfsf.com doesn't resolve to any ip. If I were to try to connect to it, it would resolve butternothingsdfsdfsf.com.myhostname.net. This only happens when hostnames don't resolve or IP's don't exist which is causing a few problems with applications. How do I fix this issue? Any help would be highly appreciated.
Thanks.

---

### Post by Puck7 on 2009-12-19
Seems to me that you're having DNS issues. You could try using a custom DNS server, like [opendns]("http://www.opendns.com/"), or [google's free dns]("http://code.google.com/speed/public-dns/").
[Here's]("https://store.opendns.com/setup/operatingsystem/ubuntu") the guide how to change the DNS on Ubuntu.

---

### Post by rapfnny on 2009-12-19
I fixed it, I had search myhostname.net in /etc/resolv.conf idk how it got there. But thanks!

---

