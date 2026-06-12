---
title: "Hi I have my laptop set for Xubuntu but need to make partition for windows"
date: 2012-05-31
forum: General Help
---

### Post by jcer93705 on 2012-05-31
Hi guys damn I guess I need to partition my drive to install Windows because some programs need Window to work. I have Xubuntu setup on my laptop. I need step by step to dual boot with xubuntu first. Thanks.

---

### Post by Mark Phelps on 2012-05-31
It's generally better to install Windows first because Ubuntu can then add a menu item to boot Windows, but Windows can not do that for Ubuntu.

You will have to create some space for a Windows partition.  Since you can not manipulate partitions while they are in use, you will have to boot from an Ubuntu LiveCD or LiveUSB and select GParted (Gnome Partition Editor).

Once that opens, you will see a list of partitions.  Select the one on the left and choose the option to shrink it down -- to leave room for Windows.  Gparted is very S...L...O...W  So, don't interrupt it and don't get impatient. Make sure your laptop doesn't lose power or shutdown in the process or your partitions will get corrupted and you won't be able to boot in anymore.

After the free space is created, you will have to shut down the laptop and reboot it from  the Window media (CD or DVD) and use that to install in the free space.

---

### Post by ajgreeny on 2012-05-31
And BACKUP, BACKUP, BACKUP.

I know I am repeating myself, but it is very important.  You could even clone your xubuntu disk/partition with clonezilla, just in case, though usually gparted works fine but very SLOW as Mark said.

---

