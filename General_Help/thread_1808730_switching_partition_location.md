---
title: "switching partition location?"
date: 2011-07-20
forum: General Help
---

### Post by match417 on 2011-07-20
I know the title seems vague, I didn't know how to word it.

Basically I just got a new laptop (asus k52f) and I'm running 10.04 LTS on it. I just wiped windows off of the drive and partitioned it like I like it (150G for OS, 350G for storage), then put windows in virtualbox. I made the mountpoint for the storage /xtra this time and it seems I can't store or create files unless I do it via terminal. I've never tried this way before, I've always had the partition as a separate drive. I want it like I had it on my last laptop where the partition appeared in the "places" menu where USB drives appear when they are inserted, and I don't want to reinstall everything and have to configure everything like I like it again. I tried giving myself sudo privileges in "users and groups", I logged out and back in, and it didn't solve a thing, I still have the same problem. Can I change the permissions of the folder so anyone can access it? I tried that through folder properties then permissions and it is all grayed out because I'm not the superuser. If I do it in terminal isn't it like chmod something? Or is there an easier way?

Right now I have gigs of info that I keep on the partition and it's stored on my old laptop drive that I have plugged in through a sata-usb cable and powered by an old computer powersupply that I have jumpered so it works without a pc case. It's a bit of a pain to have to always plug that thing in to get stuff off of my drive, it should be on my partition. Having to access info like that takes away from the portability of a "laptop".

Thanks

---

### Post by oldfred on 2011-07-20
What format is partition?

If you mounted it at /xtra then it is part of root not part of /home, so root is the user. Only mount in media & /home show by default in Nautilus.

---

### Post by match417 on 2011-07-20
partition is ext4, same as my OS partition.

how can I change the mount location to media? and there is no way for me to change the folder permissions to where my user can use it?

---

### Post by oldfred on 2011-07-20
You can change permissions and ownership.

I prefer to mount in /mnt/data, but that has the same issue you have. But I change permissions & ownership and then link each folder back into my /home. I have all the standard /home folders like Music, Documents etc actually in my data partition. With a new install I know i have nothing in them & just delete them and then link in my folders.

This is mine, if you want to mount in /media or directly in /home under whatever name you want (xtra, data, stuff) . You will have to unmount your current mount first.
sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

Best to permanantly mount in fstab so when you reboot it still is mounted.
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

gksudo gedit /etc/fstab
# add line like after finding UUID of partition with and using mount you created like /media/xtra:
sudo blkid -L
UUID=UUIDofpart /media/xtra ext4 relatime 0 2
# then to make sure it works:
sudo mount -a
# if no errors it just returns to command line

---

