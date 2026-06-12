---
title: "no space left on device errors"
date: 2012-10-11
forum: General Help
---

### Post by MGGD on 2012-10-11
Ubuntu noob here, my computer has been acting up in the last day with a couple of errors. By searching for these errors we've determined that the inodes are full as the disk has plenty of space.

df -i gives this:

```
df: `/root/.gvfs': Permission denied
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        596848 583068    13780   98% /
udev             125002    527   124475    1% /dev
tmpfs            126821    447   126374    1% /run
none             126821      3   126818    1% /run/lock
none             126821     12   126809    1% /run/shm
/dev/sdc1      30531584   9533 30522051    1% /media/500GB_

```
and this:
du -h --max-depth=1
gives:
```
257M    ./.mozilla
4,0K    ./.icons
8,0K    ./Desktop
4,0K    ./.themes
36K    ./.pulse
84K    ./.gimp-2.6
4,0K    ./.gstreamer-0.10
4,0K    ./.gconfd
56K    ./.gnome2
4,0K    ./Pictures
4,0K    ./.tsclient
4,0K    ./.update-notifier
0    ./.gvfs
652K    ./.shotwell
1,1M    ./.gconf
12K    ./.dbus
8,0K    ./.mission-control
12M    ./.cache
4,0K    ./.fontconfig
4,0K    ./.gnupg
5,9M    ./.config
4,0K    ./.striata
6,9M    ./.openoffice.org
287M    ./.thumbnails
4,0K    ./.gnome2_private
316K    ./.evolution
712K    ./.adobe
4,2M    ./.compiz-1
16K    ./.gegl-0.0
4,0K    ./Ubuntu One
1,6M    ./.macromedia
4,0K    ./.ssh
33M    ./.local
608M    .
```

how can we fix this?

---

### Post by SlugSlug on 2012-10-11
Post output of root - not /home 


```
df -h 
``````
sudo du -sch /
```

---

### Post by Statia on 2012-10-11
No, your disk does not have plenty of space:

```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on /dev/sda1        596848 583068    13780   98% /
```Your root partition (which also holds your /home) is nearly full.
If you have it already installed, you could run bitbleach. If you haven't you probably won't be able to install it now.
Reboot to empty some caches and /tmp
Check /var/log and remove old log-files. You may even have to force a logrotate. I once found a kern.log that had grown to over 100MB.
Remove *.crash in /var/crash
Run (as root, or with sudo):
apt-get autoremove
apt-get autoclean
apt-get clean

This should give you some breathing space.
Next investigate why the system is filling up. Check if your logfiles aren't being filled, don forget ~/.xsessionerrors.

Also having your entire system on a / that is only 582MB is not a good idea.

My root partition does not hold /home, /tmp, /var, /srv and /boot and is almost 12G.
(I did install about everything and the kitchen sink)


Oops...
I see you did df -i, not df -h.
Still might want to clean up a bit and if the situation allows it reconsider your partitioning.

---

### Post by spjackson on 2012-10-11
The immediate cause of running out of i-nodes is many small files, so you need to identify where these are and see what can be removed. You don't find this by "du" because that gives the sum of sizes. For i-nodes, it's the number of files that matters (1 file is 1 i-node, no matter what the size of the file).

A common cause, but by no means the only one, of running out of i-nodes is having several versions of kernel headers on a relatively small partition.

To see whether this is a problem:
```

cd /usr/src
ls
find . | wc -l

```
If the figure is a significant portion of the overall i-node count, then this is what you should focus on. You can remove old kernel headers via a package manager (apt, synaptic etc.)

---

