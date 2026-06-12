---
title: "Share files(Read &amp; Write) in EXT4 partition"
date: 2011-05-02
forum: General Help
---

### Post by rhchia on 2011-05-02
Recently i formatted my HDD into 5 partition namely :-
1) Win Vista
2) Ubuntu /
3) Home
4) Swp
5) EXT4 (Purpose is to share files between ubuntu and vista)

I'm wondering if its possible to install Virtual Box on both OS but pointing only to 1 virtual machine.

Also if its possible to permanently mount the shared partition on both OS.

---

### Post by rhchia on 2011-05-02
anyone?

---

### Post by ~Plue on 2011-05-02
Using ext4 to share the files between the two OSs isn't really ideal as windows cant natively read/write to linux file system (could be possible with 3rd party drivers though). If you format that partition as ntfs, then both OS can read/write to it and its a simple matter of including a line in [/etc/fstab]("https://help.ubuntu.com/community/Fstab") to automount it at start up

---

