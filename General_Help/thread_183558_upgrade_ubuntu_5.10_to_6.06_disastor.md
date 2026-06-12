---
title: "upgrade ubuntu 5.10 to 6.06 disastor"
date: 2006-05-28
forum: General Help
---

### Post by cliveau on 2006-05-28
after i download the upgrade package (6.06) then install them. my computer won't even start. i have spend all day and finally find a very useful page to show us (beginner) steps by steps to go though the upgrade process. 
please check the following link before you upgrade your ubuntu 5.10 to 6.06

"http://www.psychocats.net/ubuntu/dapper.php"

---

### Post by Daniel McLaws on 2006-05-28
For me, I just followed the upgrade procedure listed on the following page"

*[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)*

After entering the following in terminal,

*gksudo "update-manager -d"*

An upgrade script took over which prepared the system, downloaded the changes, and cleaned up the old files. The result was successfull upgrade. I am typing from 6.06 now.

---

### Post by Onyros on 2006-05-28
I used the same upgrade process as Daniel, with GNOME, KDE and Fluxbox installed, with a whole lot of tweaks I had made in a somewhat unusual setup (a mini ITX system), and had a very successful upgrade. Besides a few small problems in Fluxbox, everything else worked perfectly.

The upgrade process is *ready*, but I'd advise anyone considering it to do so by using the update manager.

---

### Post by shalinmangar on 2006-05-29
[QUOTE=cliveau]after i download the upgrade package (6.06) then install them. my computer won't even start. i have spend all day and finally find a very useful page to show us (beginner) steps by steps to go though the upgrade process. 
please check the following link before you upgrade your ubuntu 5.10 to 6.06

"http://www.psychocats.net/ubuntu/dapper.php"[/QUOTE]

Here is my install experience [http://shalinsays.blogspot.com/2006/05/ubuntu-dapper-troubles.html]("http://shalinsays.blogspot.com/2006/05/ubuntu-dapper-troubles.html")

---

### Post by rcarring on 2006-05-29
Install Midnight Commander, this great tool will help you hunt around for conf files if the upgrade crashes. Its a file manager


The upgrade procedure does require

apt-get update and a reboot under Breezy as this updates the update-manager

Then you do update-manager -d from the terminal.

This lets update-manager consider beta packages.

Then you  see the button offering the upgrade to Dapper.

Upgrade

---

### Post by shalinmangar on 2006-05-29
[QUOTE=rcarring]Install Midnight Commander, this great tool will help you hunt around for conf files if the upgrade crashes. Its a file manager


The upgrade procedure does require

apt-get update and a reboot under Breezy as this updates the update-manager

Then you do update-manager -d from the terminal.

This lets update-manager consider beta packages.

Then you  see the button offering the upgrade to Dapper.

Upgrade[/QUOTE]

Thanks for the tip. I think I didn't restart after doing the updates to breezy. That may be the reason the upgrade failed. And that should be mentioned somewhere in the wiki that you should restart after updating.

---

### Post by Harold P on 2006-05-29
[SIZE=5]Warning: Dapper is still Beta software and hasn't been officially released. Upgrade at your own risk.

[SIZE=2]Sometime's it just best to wait.[/SIZE]
[/SIZE]

---

