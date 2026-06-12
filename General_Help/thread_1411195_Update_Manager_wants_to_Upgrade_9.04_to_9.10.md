---
title: "Update Manager wants to Upgrade 9.04 to 9.10"
date: 2010-02-19
forum: General Help
---

### Post by daldude on 2010-02-19
When I try to Run Update Manager it seems to be trying to Upgrade to 9.10 even though I don't click Upgrade button next to where it says New "Distribution release  9.10 is now available".
When I run Update Manager a windows pops up saying 

**"Not all updates can be installed**

Run a partial upgrade to install as many updates as possible

This can be caused by:
A previous upgrade that did not complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a Pre-release version of Ubuntu"

It has an option to either do a partial Upgrade or to close the dialog box and if I click Partial Upgrade it  asks "

**"Do you want to start the upgrade?**

1 package is going to be removed 19  new packages are going to be installed"


So I click Upgrade and then it asks 

" Please insert 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)' into the drive '/cdrom/'

So I click Cancel because I don't want to upgrade to Ubuntu 9.10 and after about 30 seconds it prompts fro the Ubuntu 9.10 disc again so I have to click Cancel again and then click Cancel on the other dialog box in order to exit Upgrade Manager.

I DON'T Want to upgrade to 9.10 but do want to update 9.04 which includes the upgrade of Firefox.

---

### Post by Tamlynmac on 2010-02-19
One thought. Open system/administration/software sources. Go to the updates tab and under "Release upgrade" select a different option.

If one were to select never, no upgrade notification or procedure would ever be displayed. This should not effect 9.04 updates.

Good Luck & hope this helps.

---

