---
title: "ubuntu software center and synaptic pkg manager problem"
date: 2012-03-27
forum: General Help
---

### Post by javaaddict on 2012-03-27
Hi friends!! Am new to ubuntu.. Am using Ubuntu 11.04 version.. If I try to open synaptic package manager it results as encountered  a problem.. and if am trying install any software in terminal(sudo apt-get install), it results as

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Even software center not loading, it just opening and left as it is..

I executed this command at last, sudo apt-get remove..

Please help me..

---

### Post by cortman on 2012-03-27
Hi javaaddict!

Please run the following in a terminal:

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

If the second command gives you any error messages, please post the full output here. Good luck!

---

### Post by Elfy on 2012-03-27
Thread closed. Please do not post duplicates, it dilutes community effort.

---

