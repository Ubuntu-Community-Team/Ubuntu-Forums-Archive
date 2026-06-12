---
title: "apt-get problems"
date: 2006-05-04
forum: General Help
---

### Post by fonz2591 on 2006-05-04
Hello, I installed kubuntu today (from suse), and I keep getting this error message:
 ```

root@aaronslinux:/home/aaron# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gij-4.0 (4.0.1-4ubuntu9) ...
gcj-dbtool-4.0: symbol lookup error: /usr/lib/libgcj.so.6: undefined symbol: _ZN4java3awt5image13VolatileImage6class$E
dpkg: error processing gij-4.0 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.0 (>= 4.0.1-2); however:
  Package gij-4.0 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnujaxp-java:
 libgnujaxp-java depends on gij (>= 3.4) | kaffe (>= 1.1.3) | sablevm | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package kaffe is not installed.
  Package sablevm is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libgnujaxp-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjessie-java:
 libjessie-java depends on libgnujaxp-java; however:
  Package libgnujaxp-java is not configured yet.
dpkg: error processing libjessie-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.0; however:
  Package gij-4.0 is not configured yet.
 java-gcj-compat depends on libjessie-java; however:
  Package libjessie-java is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnucrypto-java:
 libgnucrypto-java depends on java-gcj-compat | sablevm | kaffe (>= 1.1.1) | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package sablevm is not installed.
  Package kaffe is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libgnucrypto-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsh:
 bsh depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing bsh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.3-java:
 libservlet2.3-java depends on java-gcj-compat | java1-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
dpkg: error processing libservlet2.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on java-gcj-compat | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java2-runtime is not installed.
 libhsqldb-java depends on libservlet2.3-java; however:
  Package libservlet2.3-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjaxp1.2-java:
 libjaxp1.2-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libjaxp1.2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxerces2-java:
 libxerces2-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
 libxerces2-java depends on libjaxp1.2-java; however:
  Package libjaxp1.2-java is not configured yet.
dpkg: error processing libxerces2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxalan2-java:
 libxalan2-java depends on libjaxp1.2-java; however:
  Package libjaxp1.2-java is not configured yet.
 libxalan2-java depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
dpkg: error processing libxalan2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxt-java:
 libxt-java depends on gij | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
 libxt-java depends on libgnujaxp-java; however:
  Package libgnujaxp-java is not configured yet.
dpkg: error processing libxt-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-java-common:
 openoffice.org2-java-common depends on libxt-java; however:
  Package libxt-java is not configured yet.
 openoffice.org2-java-common depends on libxalan2-java (>= 2.6.0-1); however:
  Package libxalan2-java is not configured yet.
 openoffice.org2-java-common depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
 openoffice.org2-java-common depends on bsh (>= 2.0b4-1); however:
  Package bsh is not configured yet.
dpkg: error processing openoffice.org2-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-core:
 openoffice.org2-core depends on openoffice.org2-java-common; however:
  Package openoffice.org2-java-common is not configured yet.
dpkg: error processing openoffice.org2-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-l10n-en-us:
 openoffice.org2-l10n-en-us depends on openoffice.org2-core (>> 1.9.129) | language-support-en; however:
  Package openoffice.org2-core is not configured yet.
  Package language-support-en is not installed.
 openoffice.org2-l10n-en-us depends on openoffice.org2-core (<< 1.9.130) | language-support-en; however:
  Package openoffice.org2-core is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org2-l10n-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-writer:
 openoffice.org2-writer depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-writer depends on python-uno (>> 1.9.129); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org2-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-calc:
 openoffice.org2-calc depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-draw:
 openoffice.org2-draw depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-impress:
 openoffice.org2-impress depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-impress depends on openoffice.org2-draw (>> 1.9.129); however:
  Package openoffice.org2-draw is not configured yet.
dpkg: error processing openoffice.org2-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-math:
 openoffice.org2-math depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-base:
 openoffice.org2-base depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-base depends on java-gcj-compat | j2re1.4 | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package j2re1.4 is not installed.
  Package java2-runtime is not installed.
 openoffice.org2-base depends on libhsqldb-java (>= 1.8.0.0-2); however:
  Package libhsqldb-java is not configured yet.
 openoffice.org2-base depends on openoffice.org2-java-common; however:
  Package openoffice.org2-java-common is not configured yet.
dpkg: error processing openoffice.org2-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2:
 openoffice.org2 depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2 depends on openoffice.org2-writer; however:
  Package openoffice.org2-writer is not configured yet.
 openoffice.org2 depends on openoffice.org2-calc; however:
  Package openoffice.org2-calc is not configured yet.
 openoffice.org2 depends on openoffice.org2-impress; however:
  Package openoffice.org2-impress is not configured yet.
 openoffice.org2 depends on openoffice.org2-draw; however:
  Package openoffice.org2-draw is not configured yet.
 openoffice.org2 depends on openoffice.org2-math; however:
  Package openoffice.org2-math is not configured yet.
 openoffice.org2 depends on openoffice.org2-base; however:
  Package openoffice.org2-base is not configured yet.
dpkg: error processing openoffice.org2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-kde:
 openoffice.org2-kde depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-common:
 openoffice.org2-common depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-common depends on openoffice.org2-l10n-en-us (>= 1.9.129); however:
  Package openoffice.org2-l10n-en-us is not configured yet.
dpkg: error processing openoffice.org2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.0
 gij
 libgnujaxp-java
 libjessie-java
 java-gcj-compat
 libgnucrypto-java
 bsh
 libservlet2.3-java
 libhsqldb-java
 libjaxp1.2-java
 libxerces2-java
 libxalan2-java
 libxt-java
 openoffice.org2-java-common
 openoffice.org2-core
 openoffice.org2-l10n-en-us
 python-uno
 openoffice.org2-writer
 openoffice.org2-calc
 openoffice.org2-draw
 openoffice.org2-impress
 openoffice.org2-math
 openoffice.org2-base
 openoffice.org2
 openoffice.org2-kde
 openoffice.org2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
``` 

I have tried dist-update, and just about everyhting i could think of (*,). 

Any help would be greatly appreciated! :-| 
Thanks

---

### Post by jeremy on 2006-05-04
What do you mean by "I installed kubuntu today (from suse)"?

---

### Post by fonz2591 on 2006-05-04
I just mean, that i had previously had SuSE.  It is unrelated to the problem, other than the fact that the kubuntu is a brand-new installation.

---

### Post by aysiu on 2006-05-04
Your sources.list is messed up. Get a fresh list here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by fonz2591 on 2006-05-04
I still get the same error...

I added a mirror/key from:
[http://kubuntu.org/announcements/kde-352.php](http://kubuntu.org/announcements/kde-352.php)

I have gotten rid of them both, but i still have the same error (yes, i did apt-get update).

---

### Post by aysiu on 2006-05-04
Can you post the output of these two commands? ```
sudo apt-get -f install
cat /etc/apt/sources.list
```

---

### Post by fonz2591 on 2006-05-04
```

sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gij-4.0 (4.0.1-4ubuntu9) ...
gcj-dbtool-4.0: symbol lookup error: /usr/lib/libgcj.so.6: undefined symbol: _ZN4java3awt5image13VolatileImage6class$E
dpkg: error processing gij-4.0 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.0 (>= 4.0.1-2); however:
  Package gij-4.0 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnujaxp-java:
 libgnujaxp-java depends on gij (>= 3.4) | kaffe (>= 1.1.3) | sablevm | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package kaffe is not installed.
  Package sablevm is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libgnujaxp-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjessie-java:
 libjessie-java depends on libgnujaxp-java; however:
  Package libgnujaxp-java is not configured yet.
dpkg: error processing libjessie-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.0; however:
  Package gij-4.0 is not configured yet.
 java-gcj-compat depends on libjessie-java; however:
  Package libjessie-java is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnucrypto-java:
 libgnucrypto-java depends on java-gcj-compat | sablevm | kaffe (>= 1.1.1) | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package sablevm is not installed.
  Package kaffe is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libgnucrypto-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsh:
 bsh depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing bsh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.3-java:
 libservlet2.3-java depends on java-gcj-compat | java1-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
dpkg: error processing libservlet2.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on java-gcj-compat | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java2-runtime is not installed.
 libhsqldb-java depends on libservlet2.3-java; however:
  Package libservlet2.3-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjaxp1.2-java:
 libjaxp1.2-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
dpkg: error processing libjaxp1.2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxerces2-java:
 libxerces2-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
 libxerces2-java depends on libjaxp1.2-java; however:
  Package libjaxp1.2-java is not configured yet.
dpkg: error processing libxerces2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxalan2-java:
 libxalan2-java depends on libjaxp1.2-java; however:
  Package libjaxp1.2-java is not configured yet.
 libxalan2-java depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
dpkg: error processing libxalan2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxt-java:
 libxt-java depends on gij | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.0 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
 libxt-java depends on libgnujaxp-java; however:
  Package libgnujaxp-java is not configured yet.
dpkg: error processing libxt-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-java-common:
 openoffice.org2-java-common depends on libxt-java; however:
  Package libxt-java is not configured yet.
 openoffice.org2-java-common depends on libxalan2-java (>= 2.6.0-1); however:
  Package libxalan2-java is not configured yet.
 openoffice.org2-java-common depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
 openoffice.org2-java-common depends on bsh (>= 2.0b4-1); however:
  Package bsh is not configured yet.
dpkg: error processing openoffice.org2-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-core:
 openoffice.org2-core depends on openoffice.org2-java-common; however:
  Package openoffice.org2-java-common is not configured yet.
dpkg: error processing openoffice.org2-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-l10n-en-us:
 openoffice.org2-l10n-en-us depends on openoffice.org2-core (>> 1.9.129) | language-support-en; however:
  Package openoffice.org2-core is not configured yet.
  Package language-support-en is not installed.
 openoffice.org2-l10n-en-us depends on openoffice.org2-core (<< 1.9.130) | language-support-en; however:
  Package openoffice.org2-core is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org2-l10n-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-writer:
 openoffice.org2-writer depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-writer depends on python-uno (>> 1.9.129); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org2-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-calc:
 openoffice.org2-calc depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-draw:
 openoffice.org2-draw depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-impress:
 openoffice.org2-impress depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-impress depends on openoffice.org2-draw (>> 1.9.129); however:
  Package openoffice.org2-draw is not configured yet.
dpkg: error processing openoffice.org2-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-math:
 openoffice.org2-math depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-base:
 openoffice.org2-base depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-base depends on java-gcj-compat | j2re1.4 | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package j2re1.4 is not installed.
  Package java2-runtime is not installed.
 openoffice.org2-base depends on libhsqldb-java (>= 1.8.0.0-2); however:
  Package libhsqldb-java is not configured yet.
 openoffice.org2-base depends on openoffice.org2-java-common; however:
  Package openoffice.org2-java-common is not configured yet.
dpkg: error processing openoffice.org2-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2:
 openoffice.org2 depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2 depends on openoffice.org2-writer; however:
  Package openoffice.org2-writer is not configured yet.
 openoffice.org2 depends on openoffice.org2-calc; however:
  Package openoffice.org2-calc is not configured yet.
 openoffice.org2 depends on openoffice.org2-impress; however:
  Package openoffice.org2-impress is not configured yet.
 openoffice.org2 depends on openoffice.org2-draw; however:
  Package openoffice.org2-draw is not configured yet.
 openoffice.org2 depends on openoffice.org2-math; however:
  Package openoffice.org2-math is not configured yet.
 openoffice.org2 depends on openoffice.org2-base; however:
  Package openoffice.org2-base is not configured yet.
dpkg: error processing openoffice.org2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-kde:
 openoffice.org2-kde depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
dpkg: error processing openoffice.org2-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2-common:
 openoffice.org2-common depends on openoffice.org2-core (>> 1.9.129); however:
  Package openoffice.org2-core is not configured yet.
 openoffice.org2-common depends on openoffice.org2-l10n-en-us (>= 1.9.129); however:
  Package openoffice.org2-l10n-en-us is not configured yet.
dpkg: error processing openoffice.org2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.0
 gij
 libgnujaxp-java
 libjessie-java
 java-gcj-compat
 libgnucrypto-java
 bsh
 libservlet2.3-java
 libhsqldb-java
 libjaxp1.2-java
 libxerces2-java
 libxalan2-java
 libxt-java
 openoffice.org2-java-common
 openoffice.org2-core
 openoffice.org2-l10n-en-us
 python-uno
 openoffice.org2-writer
 openoffice.org2-calc
 openoffice.org2-draw
 openoffice.org2-impress
 openoffice.org2-math
 openoffice.org2-base
 openoffice.org2
 openoffice.org2-kde
 openoffice.org2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
aaron@aaronslinux:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
 ## Uncomment the following two lines to fetch updated software from the network
 deb http://archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe
 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
 deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe 

```

---

### Post by aysiu on 2006-05-04
Hm. That's weird. I'm not sure what to make of it.

---

### Post by fonz2591 on 2006-05-04
I think I will try installing Ubuntu, and installing kde on top of that.  Thnaks for all your help!

Btw: I probably won't install it, until tomorrow, so if anyone has any ideas, I would appreiciate it.

---

### Post by Al3xanR0 on 2006-05-04
[QUOTE=fonz2591]I think I will try installing Ubuntu, and installing kde on top of that.  Thnaks for all your help!

Btw: I probably won't install it, until tomorrow, so if anyone has any ideas, I would appreiciate it.[/QUOTE]

This may or may not work but give it a try.First I would go to your /etc/apt directory then ```
mv sources.list sources.list.old
```, next go [here]("http://www.ubuntulinux.nl/source-o-matic") to generate a new sources.list form scratch,  copy the text to a file (that you will rename to sources.list) finally ```
cp /some/folder/sources.list /etc/apt/
```

---

