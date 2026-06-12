---
title: "Changing filesystem - Using Partimage to make a copy of the data."
date: 2010-02-22
forum: General Help
---

### Post by ShakeyJake on 2010-02-22
Hey guys, very quick question.

I have my / partition on an SSD that I formatted in ext3 but I now realise that, in order to use TRIM, I need to be ext4. Can I use Partimage to make and image of the partition, format it (using GParted) and then restore the image? Basically, do Partimage files survive a filesystem change?

Thanks in advance!
Jack

---

### Post by maweki on 2010-02-22
you could change the filesystem without partitioning.

Boot to a live-cd, so that you are not using the partition you want to change.

```
sudo tune2fs -O extents,uninit_bg,dir_index /dev/sda2
sudo fsck -pf /dev/sda2
```

where sda2 would be your partition

change the partition type in your /etc/fstab to "ext4" for this partition.

And don't forget to reinstall grub:
```
grub-install --root-directory=/mnt /dev/sda
```
where sda is your harddrive

[B]Edit:
But please wait for confirmation of another forum member, because I am not entirely sure.[/B]

---

