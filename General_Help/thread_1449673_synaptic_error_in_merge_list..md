---
title: "synaptic error in merge list."
date: 2010-04-08
forum: General Help
---

### Post by theDaveTheRave on 2010-04-08
Hello all,

I'm sure I'm not the first to have encountered a problem with synaptic when I tried to load it up to install a new bit of software (in this instance help screens for OO).

However when I did I got the following error message 

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I opened the file that had the apparent prolem < /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages > it transpired it actually contained the html page for the router ?? which seemed wierd to me.

However I have recently I changed to a new ISP

So after a bit of a search, nothing explicity had my problem, and I was a bit stumped. Then I suddenly had a thought, after reading someone else how did something similar.... I then did the following....

```
sudo mv /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages_BAD

```
so as synaptic would no longer look at the bad file....

```

 sudo apt-get update

```
which I guess re-creates everything the way it should be?

```

sudo apg-get check

```

which returns no errors. When I ran this prior to doing the above steps of moving the bad file etc I simply got the same error messages again.

I then almost immediately received an update notification, which I politely performed, and everything not seems to be back to normal

I would include a copy of the file that I renamed, but I'm guessing the < apt-get check > procedure removed it....

Can anyone tell me however why the file managed to become corrupted??

David

---

### Post by lisati on 2010-04-08
Moved from "Tutorials and tips" to "General help", "solved" tag removed, and code tag fixed.

---

### Post by theDaveTheRave on 2010-04-09
lisati,

Thanks for that.

However I did solve my problem (hence the solved tag), and wanted to share the info with others. The solved tag will tell someone searching this issue that there is a worked solution, even though I don't understand why the problem occured in the first instance?

I didn't find a direct reference to this particular problem and worked out the solution after getting ideas from various other threads.

David.

---

