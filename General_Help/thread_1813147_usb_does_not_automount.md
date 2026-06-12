---
title: "usb does not automount"
date: 2011-07-27
forum: General Help
---

### Post by fbs061288 on 2011-07-27
Hi All,

My Ubuntu 10.04.2 Alternate amd64 bit installation cant seem to automount usb flashdrives but it can detect.

What I did was to add a rules in /etc/udev/rules.d/[ruletoautomount]

It can now automount but the user cant unmount using the right click then unmount

it says error: umount: /media/[labelusb] not in /etc/fstab (and you are not root)


PLEASE HELP!!!
=========================
# start at sdb to ignore the system hard drive
KERNEL!="sd[b-z]*", GOTO="my_media_automount_end"
ACTION=="add", PROGRAM!="/sbin/blkid %N", GOTO="my_media_automount_end"

# import some useful filesystem info as variables
IMPORT{program}="/sbin/blkid -o udev -p %N"

# get the label if present, otherwise assign one based on device/partition
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"

# create the dir in /media and symlink it to /mnt
ACTION=="add", RUN+="/bin/mkdir -p '/media/%E{dir_name}'"
# create a symbolic link to /media/{usb_folder} on desktop
ACTION=="add", RUN+="/bin/ln -s '/media/%E{dir_name}' '/home/aardvark/Desktop/%E{dir_name}'"

# global mount options
ACTION=="add", ENV{mount_options}="relatime"
# filesystem-specific mount options (777/666 dir/file perms for ntfs/vfat)
ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},gid=100,dmask=000,fmask=111,utf8"

# automount ntfs filesystems using ntfs-3g driver
ACTION=="add", ENV{ID_FS_TYPE}=="ntfs", RUN+="/bin/mount -t ntfs-3g -o %E{mount_options} /dev/%k '/media/%E{dir_name}'"
# automount all other filesystems
ACTION=="add", ENV{ID_FS_TYPE}!="ntfs", RUN+="/bin/mount -t auto -o %E{mount_options} /dev/%k '/media/%E{dir_name}'"

#remove the symbolic link to ~/{usb_folder}
ACTION=="remove", RUN+="/bin/rm -f '/home/aardvark/Desktop/%E{dir_name}'"
# clean up after device removal
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l '/media/%E{dir_name}'", RUN+="/bin/rmdir '/media/%E{dir_name}'"

# exit
LABEL="my_media_automount_end"
==========

---

### Post by wt8008 on 2011-07-29
You may need to add the option user or users to your mount command.

See [http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html)

---

### Post by fbs061288 on 2011-07-30
Ei Thanks for Your reply.

I already had a workaround for this actually.

What I did was to:

# mv /bin/umount /bin/[somethingelseumount]
# vi /bin/umount
       #!/bin/bash
       /usr/bin/sudo /bin/[somethingelseumount]
# chmod +x /bin/[somethingelseumount]
# then edited the /etc/sudoers to add the /bin/[somethingelseumount] to his allowed commands. 

LOL. kinda crazy but it works. user can now unmount in nautilus by right click.

---

