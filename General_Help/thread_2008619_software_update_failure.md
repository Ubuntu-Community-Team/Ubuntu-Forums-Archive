---
title: "software update failure"
date: 2012-06-23
forum: General Help
---

### Post by kjbox on 2012-06-23
I keep getting a warning icon that tells me that update information is outdated. It tells me to check for updates and see where error is. Did that and found the error, as shown here:

```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources  Hash Sum mismatch

```

I did try running apt-get update in a terminal and got the same errors as above but also something .bzip file(s) being corrupted and a suggestion to run -tvv, all that did was tell me there was no such command (I probably entered it wrongly). Now running apt-get update just gives the errors shown above.

Where do I go from here to fix this?

Thanks in advance for any help or suggestions.

---

### Post by digithal on 2012-06-23
This message mean there is a problem with the mirror you are using. Changing the mirror and re-running apt-get update should fix it. 
However, try first the suggested from [this thread](http://ubuntuforums.org/showthread.php?t=1905494), post #2.

---

### Post by kjbox on 2012-06-23
The solution mentioned in that thread worked for me too. Thanks

---

