---
title: "Make link to external hard drive"
date: 2011-02-16
forum: General Help
---

### Post by andrew-w on 2011-02-16
Hi there,

I would like to create a link to a folder on my external hard drive that doesn't fail when the hard drive is not plugged in.

Basically I store all my videos on my external HDD and I want to link the videos folder on the HDD to my '~/videos' folder for whenever the device is plugged in but then when it is not it just behaves as a normal folder.

It's not urgent or massively important, but it would just be nice.

Anyone got any ideas?

Cheers.

---

### Post by tredegar on 2011-02-16
> Basically I store all my videos on my external HDD and I want to link the videos folder on the HDD to my '~/videos' folder for whenever the device is plugged in but then when it is not it just behaves as a normal folder.
I don't think you can (easily) make it work like this with a videos _directory_ on the external HDD, but it is easy with a videos **partition** on the ext. HDD.

Create a partition on the ext HDD.
Format it as **ext4**, mount it, then copy your videos to it.
Unmount it.
Make a line for it in **/etc/fstab**
```
UUID=.....   /home/andrew/Videos   ext4    defaults        0       2
```

When it is plugged in, it should be mounted at **/home/andrew/Videos** with the external HDDs videos available. The previous content of your Videos directory will be hidden (but still there "underneath" the mountpoint).

When it is unmounted, you will again see the files in [B]/home/andrew/Videos
[/B]
If this is too complicated, or not what you want, you could just do
```
ln -sT /media/extdrive/path/to/Videos /home/andrew/Videos/ExternalVideos
```
ExternalVideos will have files in it when the drive is plugged in, otherwise it will be a "broken link".

---

### Post by DanneStrat on 2011-02-16
You can try to make a symlink(symbolic link)

in your '~/videos' folder pointing to a directory on

your external drive.


First you need to know what your drive is mounted as(sdb, sdc 

etc.)

Connect your external drive.

Then in a terminal do:

```
sudo fdisk -l
```

Identify your drive.

Next you want to make the link.

An example on making a link:

If you have a video folder on drive "sdb" and would like

to place a symlink in your '~/videos' folder, you would do:

```
sudo ln -s '/media/sdb/videos/' '/home/yourusername/videos/videos external hdd'
```

Then you would have a symbolic link called "videos external hdd"

in your videos folder.

Good luck!

---

