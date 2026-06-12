---
title: "clone hard drive to another"
date: 2006-02-23
forum: General Help
---

### Post by asus on 2006-02-23
is there a way that i can clone my ubuntu drive .. that is only 20 gb.. and is slow.. to a new 200 GB HD.. i was not so sure weather or not i was going to use ubuntu over windows.. but i love it and want to get rid of windows and clone that config i have so i dont have to do a compleat reinstall.. thanks

---

### Post by frodon on 2006-02-23
There are several ways to do that :

1- you can make tar of your ubuntu partition and untar it to your new drive thanks to the live CD and then reintall grub to boot and use your new drive : [http://doc.gwos.org/index.php/Backup_restore_system](http://doc.gwos.org/index.php/Backup_restore_system)

2- you can use [partimage]("http://www.partimage.org/") or any other backup software like mondo or norton ghost which support ext3 in the latest version. but you will need also to reinstall grub.

To re-install grub you can use this way : [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by rattking on 2006-02-23
easy
partition and format your new drive
mount it
cp -ax / /new-disk
that will copy everything on the / partition
make sure /newdisk/proc is empty
when its done edit /newdisk/etc/fstab to point / to your new partition
reboot then edit grub to point to your new partition and boot it
check everything works 
then edit /boot/grub/menu.lst to reflect your new boot device.. so you wont have to change it everytime you reboot
if you plan on removing the old 20 gig then youll need to install grub on the new drive with
grub-install /dev/wherever

full howto here [http://www.storm.ca/~yan/Hard-Disk-Upgrade.html](http://www.storm.ca/~yan/Hard-Disk-Upgrade.html)

---

