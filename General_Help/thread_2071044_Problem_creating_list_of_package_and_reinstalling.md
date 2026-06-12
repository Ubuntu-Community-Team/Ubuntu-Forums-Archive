---
title: "Problem creating list of package and reinstalling"
date: 2012-10-14
forum: General Help
---

### Post by antimojv on 2012-10-14
The following command create a list of installed packages on a machine, and then reinstall the same packages in another machine (or the same).
It seems that the command work fine on Ubunt 32 Desktop , but on Ubuntu amd64 (Desktop) the sudo apt-get dselect-upgrade tell me that he need to uninstall a lot of packages (even unity unity-2d unity-common!! ) even if in the list of packages those packages are present. Even if those command are give in sequence on the same computer, they work fine in a 32 bit environment, and seems to fail in a 64 bit environment. May be i have miss something

sudo dpkg --get-selections > installed-software
sudo dpkg --set-selections < installed-software
sudo apt-get dselect-upgrade

Any suggestion?

---

### Post by Cheesemill on 2012-10-14
Can you post your installed-software file.

If you are creating the file on a 32-bit machine and then trying to use it on a 64-bit machine it may be trying to install the 32-bit packages (which could cause removal of the 64-bit packages).

---

### Post by antimojv on 2012-10-14
Thk for the answer :)
. 
The problem happen even if i give the command on the same machine. (i.e create a list and try to reinstall the same packages on the same machine with this 3 command give in sequence on the same machine).
It didn't happen on a Ubuntu 32 bit version.
Ubuntu.

---

### Post by antimojv on 2012-10-14
I do one test with a fresh installation of Ubuntu 64 bit on VMWare without applyng any updates and the problem didn not show. Attached the packages list. In a few minutes i will do same test with all updates applied

---

### Post by antimojv on 2012-10-14
No problem after update, so it seems related to the packages i have installed after the installation. Any hint?

---

### Post by Cheesemill on 2012-10-14
The only thing that I can think of (I've only had a quick scan of your package lists) is that your list in post #3 contains some de-install declarations for packages that are part of the ubuntu-desktop metapackage. These could be somehow forcing de-installation of the entire ubuntu-desktop package dependencies.

---

### Post by antimojv on 2012-10-14
Ok understand, i saw in the first attachment the deinstall "command" that could lead to weird dependencies deinstallation.

So the problem seems related to some packages i have installed on this Computer , it didn't happen in other machine (Laptop, Virtual Machine) whit the same Ubuntu Version.
This could be a situation in which i'm able to post a new bug?
Or may be it's a normal behaviour because some packages depend on ubuntu-desktop metapackage and whenever we deinstall them there is no way to stop ubuntu-desktop metapackage deinstallation? Sorry i have no experience on this argument :(.

As far as i know this problem never happen on 32 bit machine (but the packages installed were probably different), but may be i need to check if i only use official repository or similar thing before tryng to open a bug report?

Thank you for your patience.

---

