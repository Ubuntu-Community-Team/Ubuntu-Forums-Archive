---
title: "404 Error When Updating"
date: 2006-03-17
forum: General Help
---

### Post by GoUbuntu on 2006-03-17
When getting the latest updates, it get an error on 6 of the 13 files.  The first error is:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.12.1-0ubuntu1.2_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.12.1-0ubuntu1.2_i386.deb)
  404 Not Found

All the other errors are similar.

I've checked out the URL, the file is there and I can download the it. How do I get synaptic to get the file from the URL?

I've tried running the update multipe times.


Thanks,

GoUbuntu

---

### Post by GoUbuntu on 2006-03-17
OK, I got it working using the following (may have been a coincidence) :

1. I went intno Synaptic Package Manager.
2. Searched for the first file that had the error.
3. Found it and marked for upgrade.
4. Applied the changes (the file was upgraded).
5. Ran the system update - it downloaded all files as it should have.


GoUbuntu

---

