---
title: "Bad day: Package manager"
date: 2010-07-01
forum: General Help
---

### Post by kneewax on 2010-07-01
Hi Guys,

Its been a bad day for my 10.04 box and I am now stumped.

First thing this morning I let Update manager do its thing but found that the latest linux-image update failed.  I finally got that fixed and it appeared to finish the update OK.  I was able to use the Package Manager to install the latest .deb of Virtualbox.

However I was attempting to install Chrome (due to seperate problem with FF crashing to desktop every 20 seconds)as a second browser and I got this message:

```

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

```

However running that command gives this:

```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```
and I am at a loss as to how to fix it.

Any ideas folks?

---

