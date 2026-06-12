---
title: "Mirror issue"
date: 2011-08-26
forum: General Help
---

### Post by madara on 2011-08-26
yesterday installed ubuntu 11.04 Desktop 64bit on my machine but im getting the below error when doing sudo apt-get update : 

[HTML]Ign http://mirrors.rit.edu natty-security/universe Translation-en
Fetched 1 B in 22s (0 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirrors.rit.edu_ubuntu_dists_natty_universe_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.[/HTML]

also below when trying to play avi file and mplayer requesting for some codec and then requesting for package update below occur :

[HTML]W:Failed to fetch gzip:/var/lib/apt/lists/partial/mirrors.rit.edu_ubuntu_dists_natty_universe_binary-amd64_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/HTML]

I tried many things like changing to over 10 different mirrors.

Any one may help me ?

Also i was using ubuntu 32bit without any issue.

---

### Post by madara on 2011-08-26
also when i removed the /var/lib/apt/lists/partial/mirrors.rit.edu_ubuntu_dists_natty_universe_binary-amd64_Packages

and tried to update again i received below error 

99% [1 Packages bzip2 0 B] [Waiting for headers]                                                                                                 40.8 kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

---

