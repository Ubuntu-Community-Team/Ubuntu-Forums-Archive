---
title: "Best directory set up for media"
date: 2009-07-13
forum: General Help
---

### Post by bear24rw on 2009-07-13
Hey i'm wondering what everyone thinks is the best set up for storing movie, music, pictures, programs (zipped installs), etc..

i current have them all on a 1TB drive that is full. Im going to be getting two 1.5TB drives soon and was wondering how you think the directories should be layed out.

here what im thinking maybe,
one 1.5tb will be movie backup and other system backup
one 1.5tb will be for movies (maybe also music)
one 1tb will be for everything else

how would you suggest i mount everything (and what under what named) currently my 1tb is mouned under /mount/media but i would like to move everything back to /media  what should i call the mount folders when i switch to using the 3 drives as described above?

---

### Post by GoldenSun on 2009-07-13
I say just have one 1.5 tb dedicated towards movies and have the other one rsynch with it.
Have the 1 tb for progs, music, pics, sys backup.  

You could also just use both 1.5 tb for movie storage (half and half by alphabet) and have friends keep tb's of the same movies, so it's kindof like backing up.

---

### Post by SuperSonic4 on 2009-07-13
> **bear24rw said:**
> Hey i'm wondering what everyone thinks is the best set up for storing movie, music, pictures, programs (zipped installs), etc..

i current have them all on a 1TB drive that is full. Im going to be getting two 1.5TB drives soon and was wondering how you think the directories should be layed out.

here what im thinking maybe,
one 1.5tb will be movie backup and other system backup
one 1.5tb will be for movies (maybe also music)
one 1tb will be for everything else

how would you suggest i mount everything (and what under what named) currently my 1tb is mouned under /mount/media but i would like to move everything back to /media  what should i call the mount folders when i switch to using the 3 drives as described above?

What space you allocate depends on the proportion of what's on your drive now.

As a random guess

[COLOR="Red"]_sda_[/COLOR]
400gb: music backup
600gb: system

[COLOR="Red"]_sdb_[/COLOR]
1.2tb: movie backup + movie archive
300gb: system backup

[COLOR="Red"]_sdc_[/COLOR]
900gb: movies
600gb: music


but of course it depends how you use them.

When you boot up you'll need to run ```
sudo fdisk -l
``` to find out which is sda, which is sdb and which is sdc.

Also you need to create the folders in /media by running (one line at a time)```
cd /media
sudo mkdir Music\ Backup Movie\ Backup Movies Music Music\ Backup
```

Which will create folders in /media with the same names as I put above (obviously you can change these)

Now you have to edit fstab so they mount on boot (if you want this)

Back up fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

Edit fstab using **one** of the following commands (or as root in your favourite text editor)
```
sudo nano /etc/fstab
gksu gedit /etc/fstab
```

You will need to add a line for each one, if you want (for example) /sdb1 to be ntfs and /sdc2 to be ext3 then add the following lines

```
/dev/sdb1  /media/Movie\ Backup ntfs-3g defaults        0 0
/dev/sdc2 /media/Music ext3 defaults 0 0
```

Exit and either reboot or use ```
sudo mount -a
``` to mount all drives in fstab that are not mounted already.

---

