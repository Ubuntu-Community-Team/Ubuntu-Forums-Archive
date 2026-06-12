---
title: "Why can't I download anything from add/remove installer?"
date: 2009-10-29
forum: General Help
---

### Post by xenos_12345 on 2009-10-29
whenever i try to download something it comes up with this message:

E: /var/cache/apt/archives/p7zip-full_4.57~dfsg.1-1_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

can anyone help me???

it also does this wen i try 2 install the updates to my ubuntu 9.04 computer

---

### Post by Wiebelhaus on 2009-10-29
> **xenos_12345 said:**
> whenever i try to download something it comes up with this message:

E: /var/cache/apt/archives/p7zip-full_4.57~dfsg.1-1_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

can anyone help me???

it also does this wen i try 2 install the updates to my ubuntu 9.04 computer





Always check [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/a52dec/+bug/383735")

---

### Post by xenos_12345 on 2009-10-29
yes but HOW do you solve this problem?

---

### Post by Wiebelhaus on 2009-10-30
> **xenos_12345 said:**
> yes but HOW do you solve this problem?

```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0
```

---

