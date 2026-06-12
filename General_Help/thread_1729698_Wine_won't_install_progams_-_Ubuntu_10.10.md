---
title: "Wine won't install progams - Ubuntu 10.10"
date: 2011-04-15
forum: General Help
---

### Post by buddhuu on 2011-04-15
I had Wine working fine on a previous install of Maverick, but since the most recent time I installed I get the following message when I try to use Wine to install the very few Windows apps that I can't live without.

```
Archive:  /home/rick/Downloads/Spotify Installer.exe
[/home/rick/Downloads/Spotify Installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/rick/Downloads/Spotify Installer.exe or
          /home/rick/Downloads/Spotify Installer.exe.zip, and cannot find /home/rick/Downloads/Spotify Installer.exe.ZIP, period.
```

Obviously, I have downloaded the packages before attempting to install.

---

### Post by ~Plue on 2011-04-15
its opening the exe with the archive manager - file association issue
right click the exe > open with other application > choose 'wine application loader' and check 'remember this application for...'
(make sure you got wine installed first!!)

good luck

---

### Post by buddhuu on 2011-04-15
Ah, ya beauty! Sorted.

Now I have Spotify and TopStyle back, and I am happy!

Thanks very much indeed for the speedy assistance. :)


(Marking as solved)

---

