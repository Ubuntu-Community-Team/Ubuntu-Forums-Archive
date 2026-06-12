---
title: "Changing owner/ permissions for another partition"
date: 2006-03-21
forum: General Help
---

### Post by JSVH on 2006-03-21
Hello,
I'm new to Linux and Ubuntu. Installed Ubuntu about a month ago and have barley touched my windows partition since. This forum has been a great help and I have found a lot of answers here. However despite searching I have been unable to solve this one.

On my laptop I have two hard drives with four partitions between them. hda1 is my Windows partition (vFat), hda2 is swap, hda3 has the Ubuntu root (ext3), and hdc1 is for media, mostly music (vFat).

I have been unable to write to hda1 or hdc3 unless I swich to root. It is getting annoying to have to switch to root every time, even with the scripts. I have tried using chmod to change permissions, but when I try to delete a file it says: "/mnt/hdc1/file.mp3 cannot be deleted because you do not have permissions to modify its parent folder." And if I try to change owner all I get is "chown: changing ownership of `hdc1': Operation not permitted" Any ideas?

Thanks!
John

---

### Post by ZylGadis on 2006-03-21
open /etc/fstab and replace "default" with "iocharset=utf8,umask=000" like this (taken from mine):

/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000        0       0

Works for me.

---

### Post by Sutekh on 2006-03-21
You need to open a **Terminal** window.  It should be found in the **Applications -> Accessories** menu.  Alternatively you can press **Alt**+**F2** on your keyboard and type **gnome-terminal** to open the same.

Then you can edit your **/etc/fstab**.  fstab is a configuration file that contains information regarding your partitions and where they should be mounted.

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using **gedit, nano**, whatever you wish
```
sudo gedit /etc/fstab
```

Once you have opened the fstab then you need to change the lines correpsonding to the FAT partitions

You should change the lines to ones similar to these
```
[COLOR="Blue"]/dev/hda1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0

[COLOR="Blue"]/dev/hdc1[/COLOR]    [COLOR="Red"]/media/music[/COLOR]     [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hda1[/COLOR] and [COLOR="Blue"]/dev/hdc1[/COLOR] - are the locations of the partitions

 - [COLOR="Red"]/media/windows[/COLOR] and [COLOR="Red"]/media/music[/COLOR] - these are the folders where the partitions will be *mounted*.  If these folders don't exist you will need to create them yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
sudo mkdir [COLOR="Red"]/media/music[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.


Once you've modified the /etc/fstab, you can save it and issue the command```
sudo mount -a
```This re-mounts the partitions, without you having to restart your computer.

---

### Post by JSVH on 2006-03-21
Thank you! that worked great!

---

### Post by Shampyon on 2006-03-22
That's gotta be one of the most newbie friendly replies I've ever witnessed.
Fantastic job, Sutekh.

---

### Post by Sutekh on 2006-03-22
Welcome guys, I'm very glad it was helpful to you.

---

