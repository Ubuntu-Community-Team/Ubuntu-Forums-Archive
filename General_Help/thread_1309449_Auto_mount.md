---
title: "Auto mount"
date: 2009-11-01
forum: General Help
---

### Post by quimkaos on 2009-11-01
yes i'm a PITA... how can i auto-mount drives/partitions?
What i'm trying to do is auto-mount an NTFS disk and a partition (that has ruindows in it) so i can share files automatically betewen OSs without having to mount and enter password every time i want to use from a linux program ... exemple: a folder with music... if i want to open it from any program i have to first mount the partition

---

### Post by The Funkbomb on 2009-11-01
What you want to do is create a mount point and then point to that mount point using fstab.

So the first thing you want to do is create the mount point.  I'll use my own system as an example.

```
cd /
mkdir /mnt/share/

```

We now have our mount point.  Now, we need to get the drive ID.  The easiest way to do this is just to go into gparted.  If you don't have gparted, install it.  I'm pretty sure it's just apt-get install gparted.

Open gparted by going to System>Administration>Gparted.  Figure out what the drive name is.  Chances are it's something like /dev/sda1  Pick out the right one.

Once you have the right partition, it's time to edit fstab.

```
sudo gedit /etc/fstab
```

You're going to add a line to it.

First thing is your device name.  In this case, since mine is sda1, I would type /dev/sda1

Next, we need to choose the mount point.  We already made the directory so we're going to put /mnt/share/

Now, we need to choose the file system.  Since it's NTFS, just type ntfs.

Under options, copy this without the quotes "defaults,locale=en_US.utf8"

For dump and pass, put in 0 and 0.

Save the file and reboot.  The drive should now be mounted.

The last step is making it easily accessible.  Open up nautilus.  Go to /mnt/ and drag share into the left hand column under the line break under places.

That should do it.

---

### Post by CoreyB. on 2009-11-01
Or you could install ntfs-config, it gives you an easy clean interface.

---

### Post by DeMus on 2009-11-01
Try this, it always worked for me:

**_[COLOR="Red"][SIZE="3"]Auto mount Windows disks[/SIZE][/COLOR]_**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by quimkaos on 2009-11-01
:D

thanks!

---

