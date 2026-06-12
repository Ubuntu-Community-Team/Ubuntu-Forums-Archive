---
title: "Won't update after failed+crashed update."
date: 2011-07-27
forum: General Help
---

### Post by LotSX on 2011-07-27
> I failed an update and my computer crashed, and my update manager won't let me do a partial upgrade. When I press close:
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I open Synaptic Package Manager:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run sudo apt-get install -f:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

When I run sudo dpkg --configure -a:
dpkg: error: parsing file '/var/lib/dpkg/updates/0178' near line 0: E0F after field name`'

What do I do?


Now I'm getting this error:
Package operation failed

The installation or removal of a software package failed.


installArchives() failed: 
Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libreoffice-impress' is missing final newline

What do I do?

---

### Post by plucky on 2011-07-27
> **LotSX said:**
> I failed an update and my computer crashed, and my update manager won't let me do a partial upgrade. When I press close:
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I open Synaptic Package Manager:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run sudo apt-get install -f:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

When I run sudo dpkg --configure -a:
dpkg: error: parsing file '/var/lib/dpkg/updates/0178' near line 0: E0F after field name`'

What do I do?


Open a terminal and run ```
sudo rm /var/lib/dpkg/updates/*
```

After that run ```
sudo dpkg --configure -a
``` and see if that fixes it.

Good Luck

---

### Post by LotSX on 2011-07-27
It worked, thanks a bunch!

EDIT: Except now I'm getting this error:
Package operation failed

The installation or removal of a software package failed.


installArchives() failed: 
Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 41%%
Extracting templates from packages: 82%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libreoffice-impress' is missing final newline

---

### Post by plucky on 2011-07-27
> EDIT: Except now I'm getting this error:
Package operation failed

What command are you using?

Run from a terminal ```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
``` and if you get any errors,post the output of those commands.

Good Luck

---

### Post by LotSX on 2011-08-04
I was using update manager when getting that error message.

After I ran:
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade

I got this:
Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libreoffice-impress' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by plucky on 2011-08-05
> **LotSX said:**
> I was using update manager when getting that error message.

After I ran:
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade

I got this:
Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libreoffice-impress' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

Open Software Sources either through the Synaptic Package Manager or Update Manager and change your Download Server to the Main Server.

Then run ```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

again.

If that works,don't forget to change the server back to your local server so you can get the faster downloads.

Good Luck

---

### Post by LotSX on 2011-08-22
Same error,

Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libreoffice-impress' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

Also: Why is it that I can't install the other updates when I disable installing libreoffice-impress? I tried that too with Update Manager and it still gives error on libreoffice-impress and won't let me install the other updates.

---

### Post by raja.genupula on 2011-08-22
sounds like error in the source list

---

### Post by LotSX on 2011-08-22
How do I fix that?

---

### Post by raja.genupula on 2011-08-22
ok open synaptic package manager , in the quick-filter give **libreoffice-impress** . click at mark for re-installation and re-install it

---

### Post by raja.genupula on 2011-08-22
and then do the update again , let us know what you got

---

### Post by LotSX on 2011-08-22
It will only allow me to mark for upgrade or mark for complete removal.

---

### Post by raja.genupula on 2011-08-23
ok remove it and re install it dont go for upgrade . may be you gonna face dependencies problem . just re-install it by removing .

---

