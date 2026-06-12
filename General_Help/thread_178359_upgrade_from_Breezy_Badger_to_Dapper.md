---
title: "upgrade from Breezy Badger to Dapper"
date: 2006-05-17
forum: General Help
---

### Post by Wim De Coninck on 2006-05-17
after entering gksudo update-manager -d  Ubuntu starts the upgrade, but quickly, I get the following (English/Dutch) error :

Failed to fetch [ftp://ftp2.caliu.info/backports/dists/b](ftp://ftp2.caliu.info/backports/dists/b) … ackages.gz Kan bestand niet ophalen; bericht van server: Failed to open file.
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/b](ftp://ftp2.caliu.info/backports/dists/b) … ackages.gz Kan bestand niet ophalen; bericht van server: Failed to open file.
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/b](ftp://ftp2.caliu.info/backports/dists/b) … ackages.gz Kan bestand niet ophalen; bericht van server: Failed to open file.
Failed to fetch [ftp://ftp2.caliu.info/backports/dists/b](ftp://ftp2.caliu.info/backports/dists/b) … ackages.gz Kan bestand niet ophalen; bericht van server: Failed to open file.
------

And after confirming the previous error-screen : 


Traceback (most recent call last):

  File "/tmp/tmpNS-3My/dapper", line 28, in ?
    app.run()

  File "/tmp/tmpNS-3My/DistUpgradeControler.py", line 499, in run
    self.dapperUpgrade()

  File "/tmp/tmpNS-3My/DistUpgradeControler.py", line 440, in dapperUpgrade
    self.abort()

  File "/tmp/tmpNS-3My/DistUpgradeControler.py", line 421, in abort
    self.sources.restoreBackup(self.sources_backup_ext)

AttributeError: 'DistUpgradeControler' object has no attribute 'sources'

-----------------------

Result : no upgrade to Dapper.

How can this be solved ?

---

### Post by Ramses de Norre on 2006-05-17
Hmm the harder but more controlable way: sudo gedit /etc/apt/sources.list, change all mentions of breezy to dapper (accept for cd-rom line, comment that out) and do sudo aptitude update && sudo aptitude dist-upgrade.

---

