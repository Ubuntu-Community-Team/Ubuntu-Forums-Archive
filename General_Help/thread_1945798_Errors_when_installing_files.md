---
title: "Errors when installing files"
date: 2012-03-23
forum: General Help
---

### Post by joelstitch on 2012-03-23
All of a sudden I started getting this error when trying to install anything:

```
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing wireshark-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
```

---

### Post by wildmanne39 on 2012-03-23
Hi try this please:
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thanks

---

