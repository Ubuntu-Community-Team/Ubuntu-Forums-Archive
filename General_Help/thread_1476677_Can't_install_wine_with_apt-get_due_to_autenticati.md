---
title: "Can't install wine with apt-get due to autentication failures"
date: 2010-05-08
forum: General Help
---

### Post by hanha014 on 2010-05-08
Hi!

I have a problem installing wine with the command

```
apt-get install wine or
apt-get install wine1.2
```

I get the following output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract lib32nss-mdns ttf-liberation ttf-mscorefonts-installer ttf-symbol-replacement
  winbind wine1.2 wine1.2-gecko
The following NEW packages will be installed:
  binfmt-support cabextract lib32nss-mdns ttf-liberation ttf-mscorefonts-installer ttf-symbol-replacement
  winbind wine wine1.2 wine1.2-gecko
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.8MB of archives.
After this operation, 106MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ttf-symbol-replacement binfmt-support lib32nss-mdns wine1.2 wine1.2-gecko cabextract ttf-liberation
  ttf-mscorefonts-installer winbind wine
Install these packages without verification [y/N]?  
E: Some packages could not be authenticated
```

I have not installed wine yet, so if someone wants to verify something in my installation thats alright but what I suspect is that it might be something wrong with the hash for the files.

---

### Post by Lucky75 on 2010-05-08
> **hanha014 said:**
> Hi!

I have a problem installing wine with the command

```
apt-get install wine or
apt-get install wine1.2
```

I get the following output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract lib32nss-mdns ttf-liberation ttf-mscorefonts-installer ttf-symbol-replacement
  winbind wine1.2 wine1.2-gecko
The following NEW packages will be installed:
  binfmt-support cabextract lib32nss-mdns ttf-liberation ttf-mscorefonts-installer ttf-symbol-replacement
  winbind wine wine1.2 wine1.2-gecko
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.8MB of archives.
After this operation, 106MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ttf-symbol-replacement binfmt-support lib32nss-mdns wine1.2 wine1.2-gecko cabextract ttf-liberation
  ttf-mscorefonts-installer winbind wine
Install these packages without verification [y/N]?  
E: Some packages could not be authenticated
```

I have not installed wine yet, so if someone wants to verify something in my installation thats alright but what I suspect is that it might be something wrong with the hash for the files.

Try sudo apt-get install?

---

### Post by hanha014 on 2010-05-09
I ran the command with sudo.

Found a solution though and that was to run

sudo apt-get update

apt was probably just a little bit out of sync.

---

