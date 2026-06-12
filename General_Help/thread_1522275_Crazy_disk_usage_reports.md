---
title: "Crazy disk usage reports"
date: 2010-07-02
forum: General Help
---

### Post by bgutt3r on 2010-07-02
For some reason, I randomly started getting low disk space remaining warnings. The disk usage analyzer says that my total file system can hold 98.4 GB, and that I have used 82 GB, and thus have 16.5 GB of usable space left...

However, in the actual analysis, it shows that my root file system contains only 13.7 GB of data (which I know to be the correct value).

See the screenshot of the disk use analysis please..and any help is always appreciated. Pretty sure this is a bug of some type, but I don't know what needs to be reset to fix it.

If it helps, my hard disk is 1 TB, with three 100 GB partitions (win7, Ubuntu, blank fat 32 for BSD later) and a 700 GB partition of FAT32 data. The data partition is mounted on startup.

---

### Post by bgutt3r on 2010-07-02
Should've played around more before posting... running the analyzer as root (sudo baobab) showed me three partition backups that were saved somewhere in /root/, no idea how they got there, since I tar'd them straight to a usb hdd. Apparently, disk use analyzer won't show files is doesnt have rights to, and even running as sudo didnt solve the issue, as it wouldnt list some things in my home folder.

---

### Post by artemyv on 2010-07-02
yes I have exactly the same problem. Found out I need to verify data of Disk Usage Analyzer with df utility output

---

