---
title: "problem updating"
date: 2011-06-28
forum: General Help
---

### Post by DoFa on 2011-06-28
ive been having this problem for a few days trying to update my 10.04 ubuntu.

i get this:

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

i start it up and had some keys missing which i managed to find out ho to do with gpg. 
i thought it would be the end of it but now i get:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and the message beneath:
GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/jaunty/Release.gpg)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_GB.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_GB.bz2](http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.gz)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/binary-i386/Packages.gz)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/jaunty/free/source/Sources.gz)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/jaunty/non-free/source/Sources.gz)  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/binary-i386/Packages.bz2](http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

now the cairo dock one i can sort myself and have found it already on the forums, but im struggling to work out what to do next or how to solve these problems.

any help would be greatly apreciated. :) sorry if this is in the wrong thread i couldnt find a relative one anywhere.

---

### Post by snowpine on 2011-06-28
You're using an outdated, "end of life" release. You need 10.04 or newer.

I recommend a fresh reinstall, but it is also possible to do an "end of life upgrade:"

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

(edit) if you are actually using 10.04 then your software sources are a mess! You need to delete all references to jaunty, karmic, basically anything except lucid (10.04).

---

### Post by DoFa on 2011-06-28
thanks for your fast reply i was thinking a fresh install myself, but i have tweaked my ubuntu for years and itll be a long drawn out process to get it all sorted again.

im presently running ubuntu 10.04LTS with the latest kernel ive upgraded it since jaunty, my main problem is last week i still had the option to update  to 10.10 and check any updates were available now the "10.10 is available" is gone and i can no longer update anything.

i should have been more clear at the start. my apologies. is there anyway of adding the information that the update manager needs? like gpg/etc? 


i had a look through the EOL part but as i said im not upgrading from any older distribution.

many thanks in advance

---

### Post by snowpine on 2011-06-28
Edit your software sources with your favorite text editor, for example:

```
gksu gedit /etc/apt/sources.list
```

Delete any lines that contain the word "jaunty" or "karmic". These releases are end-of-life and the repositories are going, going, GONE!

Also check the /etc/apt/sources.list.d/ folder for any additional software sources and delete any references to "jaunty" or "karmic" there, too.

Only use "lucid" software sources for 10.04! :)

---

### Post by DoFa on 2011-06-28
ok ive edited my software sources list and deleted a few items out of the folder sources.list.d restarted my computer and i still have errors when it tries to auto update:

this:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

ive attached screenshots of my software sources am i missing some keys or somthing???? still cant understand why its trying to look for jaunty backports

---

### Post by snowpine on 2011-06-28
Somewhere in your /etc/apt/ folder is a reference to Jaunty Backports. That's the only logical explanation. :)

---

### Post by DoFa on 2011-06-28
aha!!!! i have it, it was under the sources.list.save~ removed all and its working again now

big thumbs up there mate many thanks +1000 internets for you :-D

---

### Post by snowpine on 2011-06-28
YEAH! Congrats on solving the problem. :)

---

