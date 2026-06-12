---
title: "Can't unmount ntfs partitions"
date: 2011-07-10
forum: General Help
---

### Post by russgillespie on 2011-07-10
Hello,

I'm 100% new to Ubuntu, and I'm running 11.04. I just installed it a few hours ago. I'm duel booting with W7 and everything is fine in that respect.

I was reading an arcticle over at lifehacker.com which suggested using 'ntfs-config' to make ntfs partitions mount on bootup so that I can access my data partition from Ubuntu. The first time I installed ntfs-config it would not run. I uninstalled and reinstalled it and then it ran, but it didn't seem to be responding very well. I attempted to tick the partition I wanted and set it to be writeable. After I closed the app ALL my ntfs partitions were mounted, even the windows and system reserved partitions, and when I attempted to unmount them I got the following error:

Unable to unmount Data
Error unmounting: unmount exited with exit code 1:
helper failed with
unmount /dev/mapper/isw_dfjjdefcdi_RAID5p4 is not mounted (according to mtab)

I tried rebooting. I tried uninstalling ntfs-config, then reinstalling it (now it wont run again). So I'm at a loss as to what to do.

I simply want my data partition mounted on boot up and writable, not the others.

Many thanks,
Russ

---

### Post by DawieS on 2011-07-11
Welcome to the forums!:smile:

I recommend that you uninstall **ntfs-config** (it may have been useful in older (pre-9.04) versions of Ubuntu, in later versions it causes more harm than good).
Next, you will have to undo the following 2 changes made by **ntfs-config**:

1) If you still have the original **/etc/fstab** file, re-install that. If however you have overwritten the original backup (created by **ntfs-config**) with a later (modified) backup file, you may have to edit the **/etc/fstab** file to restore it. Open a terminal and type:
```
sudo gedit /etc/fstab
```Delete the lines referring to your NTFS partitions. The original **/etc/fstab** file should reference only your Boot and Swap partitions. As an example, this is the **/etc/fstab** file on my 10.04 installation:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                            <mount point>  <type>  <options>          <dump>  <pass>
proc                                       /proc           proc    nodev,noexec,nosuid 0       0
# Boot Partition 
UUID=384002b8-4a0f-4161-a602-72d85f728b31  /               ext4    errors=remount-ro   0       1
# Swap Partition
UUID=c6c9918d-0e03-4ba6-afd3-6e4dfc655bbb  none            swap    sw                  0       0

```Save, and exit the editor.

2) Unmount all partitions, and delete all the permanent mount points created by **ntfs-config** in **/media**, which is a **System-Only** folder. To make sure all partitions are unmounted, open a file browser, click on File System, then on the + at media. The included sub-folders (mount-points) should be empty. [COLOR=Red]If not, then you are going to delete your actual data in your partitions, when deleting the mount points.[/COLOR] To delete the mount points, open a terminal, and type:
```
sudo nautilus
```Browse to **/media** and delete all included sub-folders (mount points created by **ntfs-config**).
Empty the **Trash** and close the file browser and terminal. You should now be back to where you were before installing **ntfs-config**.

I do not recommend data partitions to be permanently mounted, for the sake of security and accidental damage or inadvertent deletion. Mounting (and unmounting) requires only one click. If you must include data partitions in your **/etc/fstab** file, I recommend that you use the no-auto option (for more info type man mount in a terminal).

---

### Post by russgillespie on 2011-07-11
DawieS, thank you so much for helping me with this. Your instructions were spot on and I'm back to where I started.

Russ

---

### Post by Bucky Ball on 2011-07-11
You need ntfs-3g as well as ntfs-config. ;)

---

### Post by Morbius1 on 2011-07-11
ntfs-3g is already installed and has been since I think Hardy. In fact if you mount specifying "ntfs" as the filetype it points to ntfs-3g.

ntfs-config is a very confused little utility. The first thing it asks you when you run it for the first time is if you want it to enable write support. Write support is already enabled since ntfs-3g is already installed. You have to wonder what it does when you answer yes.

---

