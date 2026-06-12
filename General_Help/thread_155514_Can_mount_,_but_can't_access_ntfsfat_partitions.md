---
title: "Can mount , but can't access ntfs/fat partitions"
date: 2006-04-05
forum: General Help
---

### Post by junglemike on 2006-04-05
Hi all. I Must say i'm new to linux, and especially to ubuntu.
All my documents and data are on partition /dev/hda9 which is ntfs. in file browser , /mnt is emplty. So i open a console, and try to mount the partition:
sudo mount /dev/hda9 /mnt
But when i try to open a /mnt folder in file manager again, i get this : > You don't have permissions necessary to view the contents of "mnt"

Q1) HOw can i get that permission.
Q2) How can i mount all needed partitions from the startup. So that right after starting gnome - all disks would be already available in the /mnt partition ?
TIA.

---

### Post by christhemonkey on 2006-04-05
If you add a line to the end of your /etc/fstab:
```
sudo gedit /etc/fstab
```
Then add:
```
/dev/hda9   /mnt/windows   ntfs      ro,auto,user,fmask=0111,dmask=0000
```
to the end.

But note, that you cannot write to an ntfs partition.
Also you may need to create the directory:
```
sudo mkdir /mnt/windows
```

---

### Post by Sutekh on 2006-04-05
[QUOTE=junglemike]Hi all. I Must say i'm new to linux, and especially to ubuntu.
All my documents and data are on partition /dev/hda9 which is ntfs. in file browser , /mnt is emplty. So i open a console, and try to mount the partition:
sudo mount /dev/hda9 /mnt
But when i try to open a /mnt folder in file manager again, i get this : 

Q1) HOw can i get that permission.
Q2) How can i mount all needed partitions from the startup. So that right after starting gnome - all disks would be already available in the /mnt partition ?
TIA.[/QUOTE]

Try
```
sudo mkdir /mnt/windows
sudo mount /dev/hda9 /mnt/windows -t ntfs -o nls=utf8,umask=0222
```
You can only get read and execute access, write access is not supported without extra applications.

To make this automatic, edit the fstab
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Then unmount the partition first
```
sudo umount /dev/hda9
```
And add this line
```
/dev/hda9   /mnt/windows   ntfs   nls=utf8,umask=0222   0   0
```
Save the file (Ctrl+O) and exit (Ctrl+X) and roumount the partitons with
```
sudo mount -a
```
Of course /mnt/windows is just my example, use whatever you like

I wouldn't recommend mounting all your partitions to /mnt, but subfolders under /mnt would be fine.  If you want to do that, just create the folders, unmount the partitions, edit the /etc/fstab and remount, using similar commands to those I gave above.

---

### Post by halfvolle melk on 2006-04-05
Hi,

1) You can change permissions with "chmod -R 755 /mnt" or ownership by "chown -R <username> /mnt"

Check "man chmod" and "man chown" for more info.

2) This should help you with NTFS:
[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

---

### Post by junglemike on 2006-04-05
Thanks guys.
I added this line to fstab and it works.

---

