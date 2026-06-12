---
title: "Update Manager Installation Error"
date: 2009-07-12
forum: General Help
---

### Post by Frayjin on 2009-07-12
Hey guys,

I am very new with using Ubuntu 9.04 and I have a problem with its Update Manager that keeps telling me that it can not find the required updates in the internet repository. Anyone here that has any idea on how to fix this problem?

Cheers for the help in advance,
Frayjin


update managers error log:
```
W: Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.23~winehq0~ubuntu~9.04-0ubuntu1_i386.deb
  404 Not Found


W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.12~rc1+git20090403-0ubuntu2_i386.deb
  404 Not Found


W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.12~rc1+git20090403-0ubuntu2_i386.deb
  404 Not Found


W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.12~rc1+git20090403-0ubuntu2_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.5.5-1ubuntu8.1_all.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.5.5-1ubuntu8.1_all.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.5.5-1ubuntu8.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.5.5-1ubuntu8.1_i386.deb
  404 Not Found

```

---

### Post by Finalfantasykid on 2009-07-12
Have you tried changing which server you are downloading from?  You can do so in the update manager settings.

EDIT:  Maybe also try doing it in the terminal

```

$ > sudo apt-get update
$ > sudo apt-get upgrade

```
I think that accomplishes the same thing

---

### Post by Frayjin on 2009-07-12
Thanks for the quick reply!

Well I did try that. But is seems I am unable to get some updates form some US repository, it says the link doesn't exist anymore.

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Hence the 404 error, the link seems to be dead. Thus rendering it impossible for me to update.

Any suggestions on what to do next? I'm out of ideas .... :(

Frayjin

---

### Post by Frayjin on 2009-07-12
Found the problem ....

Seems I had forgotten about the repository I added manually ..

```
## deb http://us.archive.ubuntu.com/ubuntu edgy universe
```

This link is outdated, by removing it the problems stopped. :)

Frayjin

---

