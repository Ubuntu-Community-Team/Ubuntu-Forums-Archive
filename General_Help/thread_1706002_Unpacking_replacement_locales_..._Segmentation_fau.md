---
title: "Unpacking replacement locales ... Segmentation fault"
date: 2011-03-13
forum: General Help
---

### Post by PigPenDe on 2011-03-13
Hi all,

after an 'apt-get update' and 'apt-get upgrade' I get the following output.

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3335kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 37579 files and directories currently installed.)
Preparing to replace locales 2.3.18.41 (using .../locales_2.3.18.42_all.deb) ...
Segmentation fault
```I did search a lot, but didn't find anything appropriate.

'dpkg-reconfigure locales', 'apt-get -f install locales', 'dpkg --configure -a' and 'apt-get --reinstall install locales" didn't help me.


Is there someone who gives me helping hand?

---

### Post by PigPenDe on 2011-03-15
Bump.

No one?

---

### Post by pqwoerituytrueiwoq on 2011-03-15
segmentation fault is a result of trying to allocate more memory than was declared for an array
at lest in c++
ex:
you declare your array to have 10 values and if you try to use more than that you get that error message
there is likely a similar issue in the install script in the deb file

---

### Post by plucky on 2011-03-15
Get it to download again by removing the packages from the archives.The easiest way is to run ```
sudo apt-get clean
``` But if you want to keep the packages already downloaded,then navigate to the directory with ```
cd /var/cache/apt/archives
``` and remove the file with ```
sudo rm locales_2.3.18.42_all.deb
```

Then run ```
sudo apt-get install -f
``` will hopefully fix the problem.

Good Luck

---

### Post by PigPenDe on 2011-03-24
Thanks for the answers and sorry for the delay on my part.

I did the steps plucky mentioned, but the error is still there.

---

### Post by PigPenDe on 2011-03-31
[Solved]

I went to /var/cache/apt/archives and made a "dpkg -i locales_2.3.18.43_all.deb".
Found this solution in a debian forum :wink:

---

