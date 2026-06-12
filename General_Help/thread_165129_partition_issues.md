---
title: "partition issues"
date: 2006-04-24
forum: General Help
---

### Post by starscalling on 2006-04-24
nekostar@dapper:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             3.7G  2.5G  1.1G  70% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  184K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-21-386/volatile
/dev/hda4              30G   48K   30G   1% /media/apple
/dev/hdb1             151G   43G  109G  28% /media/bananna
/dev/hdb2              39G  4.4G   33G  13% /media/coconut

so um
what i wanna do is del /dev/hda2 and resize /dev/hda1 to include it
:/
i cant get what parted does or watever... and hda1 is ext3

---

### Post by gerbman on 2006-04-27
[QUOTE=starscalling]nekostar@dapper:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             3.7G  2.5G  1.1G  70% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  184K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-21-386/volatile
/dev/hda4              30G   48K   30G   1% /media/apple
/dev/hdb1             151G   43G  109G  28% /media/bananna
/dev/hdb2              39G  4.4G   33G  13% /media/coconut

so um
what i wanna do is del /dev/hda2 and resize /dev/hda1 to include it
:/
i cant get what parted does or watever... and hda1 is ext3[/QUOTE]I'm assuming you mean "delete /dev/hd**b**2 and resize /dev/hd**b**1". Can you use GParted to do this? If not installed, do```
sudo apt-get install gparted
```then run it with```
sudo gparted
```The interface should be pretty intuitive, just delete hdb2 and resize hdb1 to fill the space. As usual, you should back up any critical data as messing with the partition table can result in data loss. Also, "delete" means delete...you won't have access to the data on hdb2 after you delete it and resize hdb1.

---

