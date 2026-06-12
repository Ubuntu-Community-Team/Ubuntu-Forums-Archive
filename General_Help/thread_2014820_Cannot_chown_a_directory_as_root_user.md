---
title: "Cannot chown a directory as root user"
date: 2012-07-02
forum: General Help
---

### Post by dzchimp on 2012-07-02
I created a directory as /usb
I then changed its ownership to droidzone.droidzone (me).
When I mounted a microsd card to /usb  with sudo mount, I found that it got mounted and the directory ownership changed to root. If I try changing ownership back, I get a message saying operation is not permitted.

```
sudo mkdir /usb
sudo chown droidzone.droidzone /usb
sudo mount -t vfat /dev/sdb1 /usb

ls -l /sudo chown droidzone.droidzone /usb
root@supernova:/home/droidzone# ls -l /
total 104
....
drwxr-xr-x   2 root root  4096 Jan  1  1970 usb
boot/vmlinuz-3.2.0-23-generic-pae


[droidzone@supernova]$ sudo chown droidzone.droidzone /usb
[sudo] password for droidzone: 
chown: changing ownership of `/usb': Operation not permitted

```

This is Kubuntu 12

---

### Post by WorMzy on 2012-07-02
FAT and NTFS don't support UNIX file permissions.

```
man mount
```

Read up on mount options for fat, particularly uid, gid and umask.

---

### Post by dzchimp on 2012-07-02
Ok, how do I mount it so that the current user can actually write to the microsd without assuming root privileges?


I'll rephrase my question. Right now what happens is that no matter where I try to mount my microsd card, it is being automatically changed to ownership root, even when the mount point which is on a directory (which originally had user ownership) and resides in the rootfs (ext4 partition)

---

### Post by WorMzy on 2012-07-02
...
> **WorMzy said:**
> ```
man mount
```

Read up on mount options for fat, particularly uid, gid and umask.

[http://manpages.ubuntu.com/manpages/precise/en/man8/mount.8.html]("http://manpages.ubuntu.com/manpages/precise/en/man8/mount.8.html")

---

### Post by dzchimp on 2012-07-02
Forgive me for saying this, but I'm familiar with the mount manpages. I've been using Linux and Android for quite some time now. I understand what you mean by saying an NTFS or Fat32 partition cannot have ownerships. My issue is that a non-root user cannot write to the microsd card no matter where it is mounted to.

There seems to be some error in my installation. When I insert usb and the device notifier pops up, if I try to click on it, normally Dolphin used to open up. But now I get a cryptic message stating "Could not mount the following device". In addition I cannot but mount the Fat32 device as root user. So as the user I cant write to the device. Am I crazy in assuming this is not the default behavior of Ubuntu?

---

### Post by WorMzy on 2012-07-02
> **dzchimp said:**
> There seems to be some error in my installation. When I insert usb and the device notifier pops up, if I try to click on it, normally Dolphin used to open up. But now I get a cryptic message stating "Could not mount the following device". In addition I cannot but mount the Fat32 device as root user. So as the user I cant write to the device. Am I crazy in assuming this is not the default behavior of Ubuntu?

I honestly don't know. I haven't used Ubuntu for years (I use Arch), and I've never used KDE.

But I'm telling you to use mount, not a graphical filemanager.

When you mount a filesystem, you graft the mounted filesystem over the top of the underlying filesystem. The permissions you set on the destination directory prior to mounting are irrelevant.

Here's a snippet from the man page:

```
uid=value and gid=value
              Set the owner and group of all files.  (Default: the uid and gid
              of the current process.)
```

---

### Post by dzchimp on 2012-07-02
I appreciate the help.

I did try mounting on the bash command line.

sudo mount -t vfat /dev/sdd1 /usb -O rw,users,uid=droidzone,gid=droidzone,umask=000

and several other variants of the mount options. In all cases, the ownership of the mount point is root, and I'm unable to touch a file in the newly mounted folder. The only way I can copy/delete files on the device is if I do so as root.

---

### Post by WorMzy on 2012-07-02
Try a lower case o.

```
       -o, --options opts
              Options are specified with a -o flag followed by a  comma  sepa&#8208;
              rated string of options. For example:

                     mount LABEL=mydisk -o noatime,nouser


              For  more  details, see FILESYSTEM INDEPENDENT MOUNT OPTIONS and
              FILESYSTEM SPECIFIC MOUNT OPTIONS sections.

```

---

### Post by ajgreeny on 2012-07-02
Two questions or comments.

1.  Where does the usb drive mount when you plug it in.  Normally it would automatically mount in a folder in /media, but you seem to have changed that to /usb in your root filesystem.  If it is a fat32 drive it should mount automatically as writeable unless you are mounting it with fstab and using incorrect options.  The easiest way to mount fat32 drives to the same place every time is to give the drive partitions  labels, and they will then always mount at /media/*label*

2.  The command you have shown several times in your original post is ```
sudo chown droidzone.droidzone /usb
``` when it should be ```
sudo chown droidzone[COLOR=Red]**:**[/COLOR]droidzone /usb
``` I am not certain that will make the difference or stop the command working, but it is worth checking.

EDIT:  I've just made a folder in the root filesystem and changed its owner from root to myself with the command syntax you used and it worked OK, so there is something else going on here which I can not help you with.

---

### Post by dzchimp on 2012-07-02
> **WorMzy said:**
> Try a lower case o.


I had done that, but accidentally changed the case while posting.

> **ajgreeny said:**
> Two questions or comments.

1.  Where does the usb drive mount when you plug it in.  Normally it would automatically mount in a folder in /media, but you seem to have changed that to /usb in your root filesystem.  If it is a fat32 drive it should mount automatically as writeable unless you are mounting it with fstab and using incorrect options.  The easiest way to mount fat32 drives to the same place every time is to give the drive partitions  labels, and they will then always mount at /media/*label*

2.  The command you have shown several times in your original post is ```
sudo chown droidzone.droidzone /usb
``` when it should be ```
sudo chown droidzone[COLOR=Red]**:**[/COLOR]droidzone /usb
``` I am not certain that will make the difference or stop the command working, but it is worth checking.

EDIT:  I've just made a folder in the root filesystem and changed its owner from root to myself with the command syntax you used and it worked OK, so there is something else going on here which I can not help you with.

1. It used to automount in /media/somewhere. I had not changed fstab, but it seemed to not automount for that session. It's fine now, and working after a reboot. It automounts correctly, and now the user ownership is being automatically set correctly. It seemed to have been a one time error, and now I'll never know why. :)

2. Yes, "." and ":" are interchangeable for chown. I've always been using "." since it saves me a Shift key. ;)


Thanks for the inputs.

Marked as solved (but I still dont know how ;) )

---

