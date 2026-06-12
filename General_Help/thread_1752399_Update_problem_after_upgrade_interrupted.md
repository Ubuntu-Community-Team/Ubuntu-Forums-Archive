---
title: "Update problem after upgrade interrupted"
date: 2011-05-07
forum: General Help
---

### Post by perfect_tree on 2011-05-07
Firstly, apologies if this is in the wrong subforum - it's sort of an upgrade problem but I haven't actually upgraded, for reasons which will become clear.


My laptop is sadly rather elderly and the battery is broken, so if it is unplugged it loses power and immediately turns off. Unfortunately I managed to accidentally do exactly this in the middle of upgrading from Lucid to Natty. I turned the computer back on, some automated disk checks were run, and I'm now apparently using Maverick. 

Launching Update Manager, I get the following message:

"Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu"

Clicking the "Partial Upgrade" option, the system starts to upgrade but exits with the following in the Terminal:
"dpkg: parse error, in file '/var/lib/dpkg/updates/0121' near line 42 package 'texlive-xetex':
duplicate value for 'Status' field"


Basically I have no idea what to do from here. The functions that I need from my computer are working (internet, music player) and I don't really need much more than that but I'd rather it was working. Also I can't install any updates or upgrade to Natty until this is solved.

Any ideas/help?

---

### Post by Hedgehog1 on 2011-05-08
If you have not done so already, please download the ISO and make a LiveCD or LiveUSB of Natty.

When you can set aside the time, backup your data and then do a clean install of Natty from the LiveCD or LiveUSB.

If you do not have a separate '/home' partition, setting one up makes future upgrades (and even a downgrade if ever needed) much easier: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-08
**Here is an example of installing an newer Ubuntu from the LiveCD/LiveUSB with a separate '/home' partitions.  The example uses /dev/sda5 as the '/' (root) partition, your partition number may be different:**

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


**This will give you a clean install of 'Natty', but leave your data alone.**


***The Hedge***

---

