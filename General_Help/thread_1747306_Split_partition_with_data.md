---
title: "Split partition with data"
date: 2011-05-02
forum: General Help
---

### Post by coffeholikas on 2011-05-02
Is there any way to split partition, in which my ubuntu 11.04 is.
I don't wanna loose data, but I dont wanna reinstall it too. any suggestions?

P.S. Now I have 750gb HDD, I want to split off 100gb~ for dual boot win7

---

### Post by mmad on 2011-05-02
GParted will let you resize the partition.

---

### Post by coffeholikas on 2011-05-02
Can't, I have to unmount HDD first, but I'm using it as dekstop from which I lounch gparted, so I can't change anything.

---

### Post by mmad on 2011-05-03
Boot into a GParted live disc.

---

### Post by seawolf167 on 2011-05-03
Either download and burn a GParted Live CD, or a Ubuntu Live CD. Then boot from said cd and if you are using a Ubuntu Live CD, simply select GParted from System -> Administration -> GParted.

Resize your disk to have the correct amount of unallocated space.

Once you do that, I *highly* suggest formatting the new NTFS volume with the built in Windows format utility. If you are installing your new Dual Boot Windows partition, the installer will take care of this for you.

Note that you will need to reinstall GRUB2 after you install Windows as it will blast away your GRUB install. See here for a helpful [how-to.]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

---

### Post by coffeholikas on 2011-05-03
Just split'ed HDD and install win7.
Tryed to reinstall grub, but when doing:

sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

got "Auf" error, cant remember it all now.
So I followed a tip from moderator in other post, forgot which :D It was smth simple like:

mount sd1
sudo apt-get install grub-pc

Now only ubuntu boots, and I still cant see "choose OS windows" or smth like that

---

### Post by Elfy on 2011-05-03
Try to update grub from within ubuntu in a terminal.

```
sudo update-grub
```

Should see it.

---

### Post by coffeholikas on 2011-05-03
> **forestpiskie said:**
> Try to update grub from within ubuntu in a terminal.

```
sudo update-grub
```

Should see it.

Thank You very much!

P.S. Is it possible to reduce "auto select" timer? 
And is it possible to change order of choices, that Ubuntu would always be first and Windows would be second chioce? (all recovery mode, and memory testing stuff in the end)

---

### Post by Elfy on 2011-05-03
Easy enough to change the time out - open the file to edit - in a terminal - ```
gksudo gedit /etc/default/grub
```

Find the Grub timeout line and change it.

Save and run ```
sudo update-grub
``` as previously

I've no real idea about the other issues as I no longer use grub2 - possibly, possibly not - check out some threads by drs305

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

There's a grub customizer - [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by coffeholikas on 2011-05-03
> **forestpiskie said:**
> Easy enough to change the time out - open the file to edit - in a terminal - ```
gksudo gedit /etc/default/grub
```

Find the Grub timeout line and change it.

Save and run ```
sudo update-grub
``` as previously

I've no real idea about the other issues as I no longer use grub2 - possibly, possibly not - check out some threads by drs305

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

There's a grub customizer - [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Thanks again. :)

---

