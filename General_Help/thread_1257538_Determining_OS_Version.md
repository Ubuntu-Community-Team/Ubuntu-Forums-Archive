---
title: "Determining OS Version"
date: 2009-09-03
forum: General Help
---

### Post by dizwell on 2009-09-03
If I want a script to run on, say, Ubuntu 9.04 but not on Ubuntu 8.10, how can I test for the OS version?

On Redhat, for example, I would grep the contents of the /etc/redhat-release file and if it contained '5.3', I'd do one thing and if it didn't, I'd "exit 1".

How, in other words, does one go about determining the version of Ubuntu that one is running on?

Many thanks in advance for any tips given!

---

### Post by tgalati4 on 2009-09-03
cat /etc/issue

lsb_release -a

cat /etc/motd

Any others?

---

### Post by dizwell on 2009-09-03
lsb_release -r will do nicely, thank you!

That looks to be nicely generic. And there's a man page!!

---

