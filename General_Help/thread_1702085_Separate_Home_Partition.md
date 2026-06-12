---
title: "Separate Home Partition"
date: 2011-03-07
forum: General Help
---

### Post by scouser73 on 2011-03-07
I have set up a separate **/home** partition, am I right in assuming that when a new Ubuntu release comes out that I would format the **/** partition, thus leaving my **/home** partition intact with all the folders still accessible?

---

### Post by Bucky Ball on 2011-03-07
Yes. Use manual partitioning when you are installing and make sure your /home (and /swap for that matter) are not ticked to format and you are installing to /. ;)

Keep in mind, though, that if you are upgrading some apps with the new release (for instance a new version of Firefox) your settings for that app, stored in /home, are for the older version and may have a problem with the new version. All your other data will be there as was though (but best to make a back-up before starting the process, naturally).

---

### Post by scouser73 on 2011-03-07
Thanks Bucky, much appreciated.

---

