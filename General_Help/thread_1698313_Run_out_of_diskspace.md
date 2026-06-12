---
title: "Run out of diskspace"
date: 2011-03-02
forum: General Help
---

### Post by Rob8900 on 2011-03-02
After every startup the free diskspace is always smaller.

I use Xubuntu 10.10 with ext4 filesystem. My partition is 3.5 GB and cannot use a bigger disk. The disk that i use is a CF (SSD).

Turning of the journal is no option because i may not have data curruption. 

Do someone has a solution for this. Maybe a command to clear up old journals.

---

### Post by mikewhatever on 2011-03-02
Run **sudo apt-get clean** to remove cached installation files, also remove the older kernels and headers.

---

### Post by Rob8900 on 2011-03-02
Already done apt-get clean, even autoclean and autoremove. But no changes.
There only one kernel installed.

---

### Post by mikewhatever on 2011-03-02
In that case, investigating where the space is might help, that is, if you think some free space is missing.

```
sudo du -s /* | sort -nr
```
That will print the sizs of directories under /.

If you think the logs are inflated, check with **sudo du -hs /var/log**.
On the other hand, with little space to spare, you might want to ditch Xubuntu and go minimal.

---

