---
title: "CRC Check Disk Integrity"
date: 2011-08-15
forum: General Help
---

### Post by CX23882 on 2011-08-15
Is there a utility that I can schedule to run weekly to go through my disk volumes and compare CRC32 or MD5 for all files with a previously-stored hash? (similar to FileVerifier++ on Windows) Ideally it would be able to email me the results with any mismatches.

The aim is to detect silent data corruption of my media library due to bit rot.

---

### Post by smurphy_it on 2011-08-15
did you try:

```
sudo apt-cache search md5sum
```

I don't use them, but did see some promising looking apps.

---

### Post by Bachstelze on 2011-08-15
There is no "one-step" solution that I know of, but if I had to do it here's what I would do:

1. Create a .sfv files for all dirctories containing the CRC32 of all files in that directory. Use a shell script if there's a lot of directories.

2. From the root of the filesystem, run cksfv -r.

---

