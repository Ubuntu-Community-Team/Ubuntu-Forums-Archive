---
title: "Can't log in"
date: 2011-04-09
forum: General Help
---

### Post by mtguy on 2011-04-09
I have a multi-boot system with ubuntu 10.04 as my primary partition  (where I do most of my work) and xubuntu 10.10 on a secondary partition.   I logged into xubuntu and did a few updates, and mounted my ubuntu  partition by following the instructions here:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Then when I tried to log into ubuntu, I got the following:

The ubuntu welcome screen, followed by a black screen for a few seconds.  Then a small box appeared on screen that said:

"Could not update ICEauthority file /var/lib/gdm/.ICEauthority"

The only button said "close" so I clicked it and another small box appeared saying:

"There is a problem with the configuration server.
(usr/lib/libconf2-4/gconf-sanity-check2 exited with a status of 256)"

Again, clicked on the close button.

Then got what appeared to be a login screen, but only had my host name  on it and no way to sign in.  No menu in the bar below and the only way I  could figure out how to get out was to power off and back on.

No idea what happened or how to fix it.  Help would be VERY appreciated.

---

### Post by Krytarik on 2011-04-10
> **mtguy said:**
> mounted my ubuntu  partition by following the instructions here:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Congratulations! You have shot your system partition by doing so. Not without reason the guide starts with stating:
> **Warning**: The tutorial on this page is for an internal drive that will serve as an extra *data* partition.By running the very last commands you have changed the ownerchips and permissions of all files/directories of your system partition:
> sudo chown -R jessica:jessica /storage
sudo chmod -R 755 /storageThe only way out of this is to reinstall, really! Of course you can save any important data you have at that partion by using either your Xubuntu system or the installCD.

But since you already got there, you may want to install Natty 11.04 straight away, the release of the final is set for 28th of this month, and all pre-release versions will get upgraded to it, and be treated as the same:
[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

Regards.

---

### Post by kiran r on 2011-04-10
sudo cp /etc/fstab /etc/fstab_backup  try to restore from the backup...if u have correctly followed all the steps

---

