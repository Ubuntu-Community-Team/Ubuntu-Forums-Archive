---
title: "WINE with 9.10"
date: 2009-12-17
forum: General Help
---

### Post by jwaclawsky on 2009-12-17
Where can I find information about WINE. I am trying to install wine but I am getting an error message about unresolved dependencies with wine. I have [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) in my software sources and authentication has "Launchpad PPA for Ubuntu Wine Team" in my trusted software providers.

Basically, I'd like to try out a windows game called "Sid Meier's Pirates Live the Life". But before I do this I'd like to investigate if there are any issues. I am running 9.10 on my Dell Mini 9. Any advice is appreciated. Thanks.

---

### Post by SteveDee on 2009-12-18
> **jwaclawsky said:**
> Where can I find information about WINE. I am trying to install wine but I am getting an error message about unresolved dependencies with wine. I have [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) in my software sources and authentication has "Launchpad PPA for Ubuntu Wine Team" in my trusted software providers.

Basically, I'd like to try out a windows game called "Sid Meier's Pirates Live the Life". But before I do this I'd like to investigate if there are any issues. I am running 9.10 on my Dell Mini 9. Any advice is appreciated. Thanks.

Not sure if this is the same game: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1985](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1985) but its a good place to start.

Did you try installing Wine via Add/Remove Applications or Software Centre?

---

### Post by Darael on 2009-12-18
> **SteveDee said:**
> Not sure if this is the same game: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1985](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1985) but its a good place to start.

Did you try installing Wine via Add/Remove Applications or Software Centre?

AIUI jwaclawsky has already installed wine, probably by that method (or equivalent), just doing it after adding the PPA containing the more up-to-date versions of wine. And I didn't check the link, but the WineHQ AppDB is definitely the best place to look a given program or game up.

---

### Post by SteveDee on 2009-12-18
> **Darael said:**
> AIUI jwaclawsky has already installed wine, probably by that method (or equivalent), just doing it after adding the PPA containing the more up-to-date versions of wine. And I didn't check the link, but the WineHQ AppDB is definitely the best place to look a given program or game up.

...and as I understand it, he is having problems installing Wine....that's why I asked which method he used.

---

### Post by howefield on 2009-12-18
> **jwaclawsky said:**
> Where can I find information about WINE. I am trying to install wine but I am getting an error message about unresolved dependencies with wine. I have [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) in my software sources and authentication has "Launchpad PPA for Ubuntu Wine Team" in my trusted software providers.

Does the software sources have karmic main after the url, ie.... 

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main

More info at...

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)



> Basically, I'd like to try out a windows game called "Sid Meier's Pirates Live the Life". But before I do this I'd like to investigate if there are any issues.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2719&iTestingId=10464](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2719&iTestingId=10464)

There are a few comments at the bottom of this page that might help.

---

