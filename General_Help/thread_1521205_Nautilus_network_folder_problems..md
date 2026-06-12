---
title: "Nautilus network folder problems."
date: 2010-06-30
forum: General Help
---

### Post by undecim on 2010-06-30
I'm using SFTP in nautilus to connect to my website to manage/upload files, and the transfer speed is a painfully slow 4 kB/s (that's slower than dialup!)

Meanwhile, I can transfer the same files with scp, rsync, filezilla, or sshfs and get upwards of 400 kB/s. 

Also, the same server has WebDAV. It works fine with fusedav, but Nautilus says that it's not a valid WebDAV share.

Anyone have any ideas? right now, I'm just using sshfs to connect, but it's annoying to have to manually connect each time.

Is there any way to either fix this or to make Nautilus use sshfs rather than gvfs?

---

