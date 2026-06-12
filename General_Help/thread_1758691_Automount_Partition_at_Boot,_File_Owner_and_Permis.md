---
title: "Automount Partition at Boot, File Owner and Permission Problem"
date: 2011-05-14
forum: General Help
---

### Post by -Inoe- on 2011-05-14
I have an NTFS partition from my past Windows installation (currently I have only Ubuntu 10.04 LTS Lucid Lynx in my machine) which contains my data.

Recently, I installed NTFS Configuration Tool (ntfs-config) to set it mounted automatically so that I can place my wallpapers there and access my files from applications without having to mount the partition manually first.

However, I got some problem:
- All the files are owned by the root. I can access, modify, delete, etc. but can't change file permission.
- SVG files are marked as executable, misrecognized as executable text file and "run or display" dialogue box appears when I try to open it.

My /etc/fstab file looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda1 :
UUID=dba858fa-bc37-4ea7-a58e-73c4c9e69659    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda6 :
UUID=39E515C24434ABFE    /media/MEDIA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda5 :
UUID=4aa70aa6-8f0f-48c3-bc59-16bd1bad731f    none    swap    sw    0    0



```What I need is: **having a partition that is ready at startup without messing up my configuration**.
Since I don't have Windows anymore, it doesn't have to be NTFS.
1. Should I format my partition to something else than NTFS? If so, how do I set it automounted?
2. If I stay with NTFS, what should I do with my /etc/fstab (or maybe other configuration) so that I am recognized as the owner of the files?

To be honest, I'm annoyed by the "run or display" dialogue. Changing nautilus behavior to "View executable text files when they are opened" is not a solution, since I have some executable text files in my home folder.
I started working with SVGs recently, but I don't have many of them yet, so if I have to change the file permission one by one it won't be that much of a pain (if there is a way to change them all by file extension or file type it will be good).

Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-05-15
NTFS doesn't recognize any kind of permission.
What you can do, is change the ownership of the partition's mount point:
```
sudo chown yourusername /media/MEDIA
```

---

### Post by Morbius1 on 2011-05-15
>  What you can do, is change the ownership of the partition's mount point:The permissions of the mount point will be overridden the instant the partition is mounted. That's true for Windows or Linux filesystems.

Change this:
>  UUID=39E515C24434ABFE    /media/MEDIA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0To this:
```
 UUID=39E515C24434ABFE /media/MEDIA ntfs-3g defaults,uid=1000,locale=en_US.utf8    0    0
```uid=1000 will make you the owner of the mountpoint.

Then unmount the partition:
```
sudo umount /media/MEDIA
```Then run the following command to check for errors and mount the new line in fstab ( so you don't have to reboot ):
```
sudo mount -a
```Then check it out to see if it meets your requirements.

---

### Post by -Inoe- on 2011-05-16
> **Morbius1 said:**
> ```
 UUID=39E515C24434ABFE /media/MEDIA ntfs-3g defaults,uid=1000,locale=en_US.utf8    0    0
```uid=1000 will make you the owner of the mountpoint.
Thanks :D It succeeded in making me as the owner :D

However, it looks like the problem with SVG files still exists.
> **TeoBigusGeekus said:**
> NTFS doesn't recognize any kind of permission
It is true that all the files are actually marked as executable and despite being the owner of the partition, I'm still unable to unceck the "Allow executing file as program" checkbox in the file properties' Permissions tab.
However, why doesn't the "run or display" dialogue box appear when opening PNG, JPG, and GIF files? How do we make SVG files not executable?

---

### Post by Morbius1 on 2011-05-16
Here's the thing about ntfs and how it's different from say .. ext4.

In a Linux filesystem the ownership and permissions information is embedded into the file itself. You can specify which file is executable and which is not.

In a Windows filesystem there are no Linux ownership and permissions bits to set at the file level. Instead one mounts the NTFS partition with the desired permissions and all folders and files will "inherit" the permissions of the mount itself.
> UUID=39E515C24434ABFE /media/MEDIA ntfs-3g [COLOR=Blue]defaults[/COLOR]The "defaults" in that line will ( among other things ) set the permissions to read/write/execute for every folder ( which you must have ) and every file in that partition. Linux cannot change the permissions of individual files in NTFS after the mount it can only set them at a global level.

What you can do is change the fstab entry to not have the execute bit set on files:
```
  UUID=39E515C24434ABFE /media/MEDIA ntfs-3g defaults,dmask=000,fmask=111,uid=1000,locale=en_US.utf8    0    0
```The "dmask" ( directory umask ) will make every folder rwx.
The "fmask" ( file umask ) will make every file rw.

If you do that though you will see that you may have the opposite problem that you had before: no file is executable.

---

### Post by -Inoe- on 2011-05-16
> **Morbius1 said:**
> Here's the thing about ntfs and how it's different from say .. ext4.

In a Linux filesystem the ownership and permissions information is embedded into the file itself. You can specify which file is executable and which is not.

In a Windows filesystem there are no Linux ownership and permissions bits to set at the file level. Instead one mounts the NTFS partition with the desired permissions and all folders and files will "inherit" the permissions of the mount itself.
The "defaults" in that line will ( among other things ) set the permissions to read/write/execute for every folder ( which you must have ) and every file in that partition. Linux cannot change the permissions of individual files in NTFS after the mount it can only set them at a global level.

What you can do is change the fstab entry to not have the execute bit set on files:
```
  UUID=39E515C24434ABFE /media/MEDIA ntfs-3g defaults,dmask=000,fmask=111,uid=1000,locale=en_US.utf8    0    0
```The "dmask" ( directory umask ) will make every folder rwx.
The "fmask" ( file umask ) will make every file rw.

If you do that though you will see that you may have the opposite problem that you had before: no file is executable.

Yay! Did that and I think it is good enough for now. If I got to execute something, I can just move the file to my operating system's ext4 partition first :D
I guess I should try ext4 when i get the time and space to backup my files, though :D

Thank you very much for the answer and explanation :D

---

