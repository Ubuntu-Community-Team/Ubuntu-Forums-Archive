---
title: "Uninstalling Acroread"
date: 2012-01-09
forum: General Help
---

### Post by Frobozky on 2012-01-09
I am using Ubuntu 11.04 (64 bit).  I use classic desktop.  After removing acroread (installed from Ubuntu Software Center), I get numerous error messages in .xsession-errors reading "(process:1786): WARNING **: recent-manager-provider.vala:125: Desktop file for acroread was not found."  Is there a way to stop this warning?

---

### Post by jerrrys on 2012-01-10
You can try this, open a terminal and enter:

sudo apt-get remove --purge acroread

I do not know for sure, but you may have to install acroread first, for the purge command to work.

---

### Post by Frobozky on 2012-01-11
> **jerrrys said:**
> You can try this, open a terminal and enter:

sudo apt-get remove --purge acroread

I do not know for sure, but you may have to install acroread first, for the purge command to work.



Thanks for your response.  I get the message: Package acroread is not installed, ...

I still have an .xsessions-errors riddled with "WARNING **: recent-manager-provider.vala:125: Desktop file for acroread was not found".

---

### Post by jerrrys on 2012-01-12
try

sudo dpkg -r acroread

---

### Post by Frobozky on 2012-01-12
> **jerrrys said:**
> try

sudo dpkg -r acroread


This results in the message:
"dpkg: warning: there's no installed package matching acroread"

I also tried reinstalling acroread from ubuntu software center. I then used purge but still get many .xsession warnings.

The command locate acroread gives:

/usr/lib/pymodules/python2.7/orca/scripts/apps/acroread
/usr/lib/pymodules/python2.7/orca/scripts/apps/acroread/__init__.py
/usr/lib/pymodules/python2.7/orca/scripts/apps/acroread/__init__.pyc
/usr/lib/pymodules/python2.7/orca/scripts/apps/acroread/script.py
/usr/lib/pymodules/python2.7/orca/scripts/apps/acroread/script.pyc
/usr/share/app-install/desktop/acroread.desktop
/usr/share/app-install/icons/acroread.png
/usr/share/icons/Faenza/apps/16/acroread.png
/usr/share/icons/Faenza/apps/22/acroread.png
/usr/share/icons/Faenza/apps/24/acroread.png
/usr/share/icons/Faenza/apps/32/acroread.png
/usr/share/icons/Faenza/apps/48/acroread.png
/usr/share/icons/Faenza/apps/64/acroread.png
/usr/share/icons/Faenza/apps/96/acroread.png
/usr/share/icons/Faenza/apps/scalable/acroread.svg
/usr/share/icons/airlines/apps/16/acroread.svg
/usr/share/icons/airlines/apps/22/acroread.svg
/usr/share/icons/airlines/apps/24/acroread.svg
/usr/share/icons/airlines/apps/32/acroread.svg
/usr/share/icons/airlines/apps/48/acroread.svg
/usr/share/icons/eco/apps/16/acroread.svg
/usr/share/icons/eco/apps/22/acroread.svg
/usr/share/icons/eco/apps/24/acroread.svg
/usr/share/icons/eco/apps/32/acroread.svg
/usr/share/icons/eco/apps/48/acroread.svg
/usr/share/icons/elementary/apps/128/acroread.svg
/usr/share/icons/elementary/apps/16/acroread.svg
/usr/share/icons/elementary/apps/22/acroread.svg
/usr/share/icons/elementary/apps/24/acroread.svg
/usr/share/icons/elementary/apps/32/acroread.svg
/usr/share/icons/elementary/apps/48/acroread.svg
/usr/share/icons/elementary/apps/64/acroread.svg
/usr/share/icons/oxygen/128x128/apps/acroread.png
/usr/share/icons/oxygen/16x16/apps/acroread.png
/usr/share/icons/oxygen/22x22/apps/acroread.png
/usr/share/icons/oxygen/32x32/apps/acroread.png
/usr/share/icons/oxygen/48x48/apps/acroread.png
/usr/share/icons/oxygen/64x64/apps/acroread.png
/usr/share/icons/split/apps/16/acroread.svg
/usr/share/icons/split/apps/22/acroread.svg
/usr/share/icons/split/apps/24/acroread.svg
/usr/share/icons/split/apps/32/acroread.svg
/usr/share/icons/split/apps/48/acroread.svg
/usr/share/pyshared/orca/scripts/apps/acroread
/usr/share/pyshared/orca/scripts/apps/acroread/__init__.py
/usr/share/pyshared/orca/scripts/apps/acroread/script.py

---

### Post by jerrrys on 2012-01-12
Hi Fro:

I loaded and removed acroread thru the software center and pertty much got the same leftovers.  Never did get "recent-manager-provider.vala:125"  warning in .xsession.  I just went ahead and manually removed all leftover packages.  So I say for you to do the same with either "gksudo nautilus" or "rm /path/to/folder" and see if your warning disappears.
[ATTACH]210739[/ATTACH]

and for good measure:

    Remove all the packages from /var/cache/apt/archives and /var/cache/apt/archives/partial folders:

    sudo apt-get clean

    Remove all expired packages from /var/cache/apt/archives and /var/cache/apt/archives/partial that are no longer available for download:

    sudo apt-get autoclean

"Not available for download" does not mean the user should save them - normally these files have been replaced or are no longer needed.

    Remove unneeded dependencies which are no longer needed:

    sudo apt-get autoremove

---

### Post by Frobozky on 2012-01-16
> **jerrrys said:**
> Hi Fro:

I loaded and removed acroread thru the software center and pertty much got the same leftovers.  Never did get "recent-manager-provider.vala:125"  warning in .xsession.  I just went ahead and manually removed all leftover packages.  So I say for you to do the same with either "gksudo nautilus" or "rm /path/to/folder" and see if your warning disappears.
[ATTACH]210739[/ATTACH]

and for good measure:

    Remove all the packages from /var/cache/apt/archives and /var/cache/apt/archives/partial folders:

    sudo apt-get clean

    Remove all expired packages from /var/cache/apt/archives and /var/cache/apt/archives/partial that are no longer available for download:

    sudo apt-get autoclean

"Not available for download" does not mean the user should save them - normally these files have been replaced or are no longer needed.

    Remove unneeded dependencies which are no longer needed:

    sudo apt-get autoremove

Thanks for the suggestions. I did all of the above and the warnings still persist.  I use nautilus elementary. Is it possible that it is calling for acroread?

---

### Post by Frobozky on 2012-01-23
> **Frobozky said:**
> Thanks for the suggestions. I did all of the above and the warnings still persist.  I use nautilus elementary. Is it possible that it is calling for acroread?

I removed libreoffice. Purged the libreoffice ppa and then reinstalled libreoffice.  After this, the acroread warning disappeared.

---

### Post by jerrrys on 2012-01-23
PPA?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purde&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purde&sa=Search&cof=FORID:9)

---

### Post by Frobozky on 2012-01-23
> **jerrrys said:**
> PPA?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purde&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purde&sa=Search&cof=FORID:9)

Yep, I had the newer version of libreoffice found in ppa:libreoffice/ppa.  For some reason removing that version and removing the ppa (ppa-purge), then reinstalling libreoffice from regular repositories stopped the acroread warnings.

---

### Post by jerrrys on 2012-01-23
and all is well; congratulations

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

