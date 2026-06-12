---
title: "can't get apt-get to get"
date: 2010-06-26
forum: General Help
---

### Post by gwpritch on 2010-06-26
Anyone seen this before? I was trying to install a package in KK:

```
sudo apt-get install ubuntu-restricted-extras
```

Packages were downloaded and unpacking then I got this:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

Now whenever I try apt-get, synaptic, all can get is this error. I can't install or remove or reconfigure anything.

Thanks for any insights.

---

### Post by stoneage on 2010-06-26
You could try this:-
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by gwpritch on 2010-06-26
Thanks, that cleared up half the problem then I replaced the status file with the status-old file and we're in business.

---

