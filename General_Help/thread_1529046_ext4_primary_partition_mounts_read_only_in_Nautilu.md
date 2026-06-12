---
title: "ext4 primary partition mounts read only in Nautilus"
date: 2010-07-11
forum: General Help
---

### Post by ddpicard on 2010-07-11
I just did a clean install of Ubuntu 10.04 and Linux Mint 9 with an ext4 (sda3) data partition to be shared between both. My issue is when I go to that partition and mount it within Nautilus it mounts read only. I've searched around but I have not found the solution. I don't have a problem mounting it using fstab and mounting at boot. But, I know I have to be doing something wrong for it not to work correctly through Nautilus.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              25G  3.2G   21G  14%  /media/7e66f3a0-e35d-40b0-8427-4abfd3b53d8a 
/dev/sda2              25G  9.8G   14G  42% /
/dev/sda3              56G   32G   21G  61% /media/data

I partitioned the drive like this. Ubuntu sda1 primary partition ext4 25gb, Mint sda2 primary partition ext4 25gb and Data primary partition 56gb. I then installed Ubuntu 10.04 first, then Mint. Both Ubuntu and Mint mount that partition as read only. I would appreciate any help.

Thanks,
Dave

---

### Post by Morbius1 on 2010-07-11
Anytime a linux file type is mounted it will mount with owner = root and permissions set to 755. The "7" allows read / write access to owner ( root ). The "5" allows read only access to everyone else.

One way to accommodate both Mint and Ubuntu is to change permissions so everyone has read / write access:

```
sudo chmod 0777 /media/data
```

---

### Post by ddpicard on 2010-07-11
Thanks Morbius1. That is what I did when I added it to the fstab.

UUID=57ebf3e9-3bbe-4c53-b52e-2f574325e6e7 /media/data ext4  defaults 0 2

I then did chmod on media. 

When I boot it auto mounts and I can read and write. 

This maybe a dumb question but I'll ask it anyway. Is it because I created sda3 as a Primary Partition?

The part that I don't understand is that in both Ubuntu and Mint the data directory under media does not exist until you mount it through Nautilus. I tried adding the data directory and chmoding it but it does not use the one I created. 

Thanks,
Dave

---

### Post by Morbius1 on 2010-07-11
It's not because you added it as a primary partition it's just how the system is set up. 

> The part that I don't understand is that in both Ubuntu and Mint the  data directory under media does not exist until you mount it through  Nautilus. I tried adding the data directory and chmoding it but it does  not use the one I created. There's two ways to mount. If you mount it through Nautilus you're mounting it on the fly and the system is set up to create a mount point dynamically. When you unmount it the mount point is gone.

If you want it to automount at boot then you need to first create a mountpoint and add the line is fstab as you have done.

Just to be clear the procedure should have been this:

If you mounted it through Nautilus unmount it first:
```
sudo umount /media/data
```At this point there should have been no /media/data. Then create a permanent mount point:
```
sudo mkdir /media/data
```And then add the line to fstab 
> UUID=57ebf3e9-3bbe-4c53-b52e-2f574325e6e7 /media/data ext4  defaults 0 2
[COLOR=Blue]EDIT: Almost forgot what the original problem was[/COLOR] :oops:
And then you need to do a sudo chmod 0777 /media/data

> I tried adding the data directory and chmoding it but it does not use  the one I created. That may have been because you didn't umount the nautilus mounted partition first.

---

