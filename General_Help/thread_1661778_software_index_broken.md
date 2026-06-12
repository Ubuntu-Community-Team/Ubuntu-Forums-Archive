---
title: "software index broken"
date: 2011-01-07
forum: General Help
---

### Post by rahulnair on 2011-01-07
i was updating my system (ubuntu 10.04) as usual...when some error occurred in the last package...and the update manager CRASHED...now every time i open the update manager,it gives me the following message

```

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

```now interestingly when i run the terminal command , it again shows me an error
as follows..
```
(Reading database ... 230036 files and directories currently installed.)
Preparing to replace kdebase-runtime-data 4:4.4.2-0ubuntu4.1 (using .../kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb) ...
Unpacking replacement kdebase-runtime-data ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/khelpcenter/searchhandlers/docbook.desktop', which is also in package khelpcenter4 4:4.2.4-0ubuntu1~jaunty3
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
now my update manager is permanently down..what should i do?
and when i open the synaptic manager it gives me the following error...:confused::confused::confused:
```

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

```pls help....

---

### Post by dino99 on 2011-01-07
open a terminal to clean the source:

sudo rm /var/cache/apt/archives/*

then update, upgrade again

---

### Post by rahulnair on 2011-01-07
thanks for the reply..
but its still not working..i remvoed evrything from the archives folder
run sudo apt-get  update
then tried to run the update manager

but the same old problem....what should i do to fix this? 
and now when i run the **sudo apt- get install -f**
its shows me the following error...
> 
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/khelpcenter/searchhandlers/docbook.desktop', which is also in package khelpcenter4 4:4.2.4-0ubuntu1~jaunty3
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by SirFunKnight on 2011-02-15
This post is a bit old, but I had this exact problem and the solution for me was this command: 

```
sudo dpkg -i --force-all /var/cache/apt/archives/kdebase-runtime-data_4%3a4.4.5-0ubuntu1_all.deb
sudo apt-get -f install
sudo apt-get autoremove

```

---

### Post by anibuntu on 2011-05-15
SirFunKnight's solution worked for me for Lucid. Thanks!

---

### Post by Capricorn1 on 2011-06-05
SirFunKnight's solution worked for me on a broken 9.10 to 10.04 LTS (Lucid) upgrade.:popcorn:

---

### Post by flint_ on 2011-12-04
SirFunKnight's solution also worked for me on a broken 9.10 to 10.04 LTS (Lucid) upgrade :P

---

