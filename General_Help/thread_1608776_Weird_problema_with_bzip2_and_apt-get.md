---
title: "Weird problema with bzip2 and apt-get"
date: 2010-10-29
forum: General Help
---

### Post by calsaverini on 2010-10-29
I'm having a problem to download the Packages.bz2 from the universe repository. 

Everytime I try to do apt-get update I get the following errors:


```

bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://www.las.ic.unicamp.br maverick/universe i386 Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 9,970kB in 4s (2,403kB/s)
W: Failed to fetch http://www.las.ic.unicamp.br/pub/ubuntu/dists/maverick/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://www.las.ic.unicamp.br/pub/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

This is a fresh ubuntu maverick instalation and I tried many, many different servers (including main server). 

The weird thing is that it appears to be a problem with all compressed files I try to download. I tried getting the Packages.bz2 file with the browser to test and got the same problem. I tried to download Firefox4 (which is a tar.bz2 file) and the same error ocurred (bzip2: Data integrity error when decompressing.) Tried tar.gz files and also got some kind of data corruption error. 

All other files I download are perfectly ok and working normally. 

I'm behind a proxy and thought that could be the problem but I can't see how. My network appears to be working properly. I have no idea what could be corrupting files so selectively (only compressed files).

---

### Post by calsaverini on 2010-11-08
I'm using my notebook in the same network, same proxy configuration, downloading packages from the same server and even using the same IP address. Everything works pretty fine. I updated the package indexes, installed things and every bzip file I download get here nicely. 

The desktop stays with the same problem above. Anyone have *any clue* what might be causing this? It seems not to be a network problem. I exhausted my knowledge here. :/

---

