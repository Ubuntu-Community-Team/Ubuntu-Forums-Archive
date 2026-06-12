---
title: "Auto mount ntfs drives..."
date: 2011-07-30
forum: General Help
---

### Post by Xstary on 2011-07-30
Hi,

I use Ubuntu 11.04 (gnome) and have a ntfs partiton that shows up in the  "places" menu that is normally in the gnome panel. But I think that  partition isn't mounted till I click on the entry in this menu (when I  want to access it from any other place, shortcuts for example, that  doesn't work).
How can I correctly mount all partitions I want on startup?
Recently I tried something in the /etc/fstab file but don't know if this is correct...

Thanks for any help!

---

### Post by Lupajz on 2011-07-30
Try messing with 

```
sudo apt-get install ntfs-config
```

then go to : 

```
Application's-->System Tools-->NTFS configuration tool's.
```

then in the window you will be able to select mounts :)

---

### Post by ~!geek!~ on 2011-07-30
I m sure above post helps you. Take it just as another suggstion.
You may use storage manager from the repository. 
To install it 
Type:
> sudo apt-get install pysdm
on terminal

To start it 
Type 
> sudo pysdm 
on terminal.

Its not specific to ntfs drives. You may configure other drives too.

---

### Post by Morbius1 on 2011-07-30
> Recently I tried something in the /etc/fstab file but don't know if this is correct...Please provide the output of each one of the following commands:

```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```And tell us if this is a dual boot with Windows. It can make a difference how you configure fstab if there is a Windows OS that is also accessing the partition.

---

### Post by Xstary on 2011-07-30
First, thanks at all of you.

Yes it is an dual boot system with Windows. Can you tell me why there is a difference then?
I think I would prefer not to use an extra tool (if its easy via fstab).


```
sudo blkid -c /dev/null
/dev/sda1: LABEL="Windows" UUID="F26CAEC36CAE8249" TYPE="ntfs" 
/dev/sda2: LABEL="Programme" UUID="0004B72B04B72318" TYPE="ntfs" 
/dev/sda3: LABEL="Dateien" UUID="71B500522BEFD2C2" TYPE="ntfs" 
/dev/sda5: LABEL="home" UUID="88a9b156-b480-4bbb-9d89-194e3bb20ebd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="swap" UUID="e70d881f-f4f5-4af1-a37d-e99454485010" TYPE="swap" 
/dev/sda7: LABEL="strich" UUID="5faa5632-615f-4792-a935-62b821df5e9b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="bbd528b3-5e5e-4b33-aabd-b386c43b7347" TYPE="ext4"
``````
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=bbd528b3-5e5e-4b33-aabd-b386c43b7347 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
#UUID=4329a4c7-2ee3-43a6-b353-f83e24047122 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# Dateien: /dev/sda3: LABEL="Dateien" UUID="71B500522BEFD2C2" TYPE="ntfs"
# diabled becuase it mounts itselfs again: /dev/sda3 /media/sda3 ntfs auto 0 0
``````
mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/USER/.Private on /home/USER type ecryptfs (ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=f4b381ae60351d2f,ecryptfs_fnek_sig=5b3998ecacea4374)
gvfs-fuse-daemon on /home/USER/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=USER)

```

Sorry too lazy to cut the useless parts ;)

---

### Post by Morbius1 on 2011-07-30
I'm guessing that this is what you want to automount:
>  /dev/sda3: LABEL="Dateien" UUID="71B500522BEFD2C2" TYPE="ntfs"If not you can use the following as a template for an ntfs partition:

[1] If the partition is currently mounted unmount it.

[2] Create a permanent mount point:
```
sudo mkdir /media/Dateien
```[COLOR=Blue][I]Note: By default anthing mounted to your home directory or /media will show a mount icon on the desktop. If you don't want that then create a mountpoint somewhere else like /mnt/Dateien or even /Dateien.

[/I][COLOR=Black][3] Edit fstab as root:
[/COLOR][/COLOR]```
[COLOR=Black]gksu gedit /etc/fstab[/COLOR]
```[COLOR=Blue][COLOR=Black]
[4] Add the following line to the end of fstab:
[/COLOR][/COLOR]```
UUID=71B500522BEFD2C2 /media/Dateien ntfs defaults,nls=utf8,uid=1000,umask=000,windows_names 0 0
```[5] Save fstab, exit gedit, and back in the terminal run the following command which will test for errors and mount the new partition.

---

### Post by Neraste on 2011-07-30
Hello folks!

As **Xstary**, I want to "automount" two NTFS hard drives and I have modified my */etc/fstab* file and added the corresponding folders in my */media*.

But by doing so, the rights of those folders in */media* are 777, which isn't very secure when you are on a network...

I've tried to use the *umask* option, but another problem appears: when you mount hard drives with *fstab*, root do it actually and then root is the owner of the directory. If you use a 700 mask then only root can read/write/execute files, not you! 770 mask doesn't work neither.

Otherwise, when you mount your drive with the desktop environment (*Place* -> *YourHardDrive*), the rights of the folder in */media* are 700 and you are the owner of the directory!

I'm quite puzzled: how does the desktop environment mount work? How can I perform the same result?

Thanks for your help!

**Edit:** take note that umask pattern is the contrary of chmod's.

---

### Post by Morbius1 on 2011-07-30
> **Neraste said:**
> Hello folks!

As **Xstary**, I want to "automount" two NTFS hard drives and I have modified my */etc/fstab* file and added the corresponding folders in my */media*.

But by doing so, the rights of those folders in */media* are 777, which isn't very secure when you are on a network...

I've tried to use the *umask* option, but another problem appears: when you mount hard drives with *fstab*, root do it actually and then root is the owner of the directory. If you use a 700 mask then only root can read/write/execute files, not you! 770 mask doesn't work neither.

Otherwise, when you mount your drive with the desktop environment (*Place* -> *YourHardDrive*), the rights of the folder in */media* are 700 and you are the owner of the directory!

I'm quite puzzled: how does the desktop environment mount work? How can I perform the same result?

You are hijacking this topic but I'll answer it because it's close to the same topic.

In the line above that I suggested for fstab I have a option:
> uid=1000That will make you the owner.
You can change the umask to:
```
umask=077
```Put them together and you have ownership = you and permissions of 700 just like you want.

BTW: 
> **Edit:** take note that umask pattern is the contrary of chmod's.That's not exactly correct. Unlike a linux filesystem, NTFS starts off with every folder and every file having permissions of 777. umask represents the permissions you want to remove. 
A "0" removes nothing
A "1" removes execute
A "2" removes write
A "4" removes read

An they are additive so a "7" ( 1+2+4 ) removes everything. A umask = 077 will remove all permissions for group and others and leave full access to the owner. If you were doing this the Jedi way you would actually split umask into it's component parts - dmask & fmask - so that folders would be executable and files would not but that's another story.
>  But by doing so, the rights of those folders in */media* are 777, which isn't very secure when you are on a network...That depends on how you set up your network and what services you are running. Your biggest threat is your browser since everything on it runs as you.

---

### Post by Neraste on 2011-07-30
Excuse me for my hijacking m(_ _)m ... Since **Xstary**'s topic was present and very close to my problem, I thought it were better to post here, as a continuity of automounting.

Anyway, thank you a lot for your answer, **Morbius1**, all works fine; *uid=1000* makes the true difference in ownership.

---

### Post by Xstary on 2011-08-08
Ok, thanks it seems to work now!

---

### Post by josempans on 2011-08-09
Hi, I will use this thread to make my question, :) Thanks in advance.
I've set up an automatic mount in a NTFS drive, everything works fine except for one thing; when I try to delete a file, the system tell me that the disk doesn't have a recycle bin; so the delete will be total. How can I setup a recycle bin for this drive?

---

### Post by Xstary on 2011-08-10
Hi, did you look here: [http://ubuntuforums.org/showthread.php?p=6405366](http://ubuntuforums.org/showthread.php?p=6405366) ?
I think I had the same problem, but forgot how to solve it.
On my ntfs partition there is a ".Trash-1000" folder. Some recommend to just create this folder to solve the problem, so you could try it.

---

### Post by Morbius1 on 2011-08-10
> **josempans said:**
> Hi, I will use this thread to make my question, :) Thanks in advance.
I've set up an automatic mount in a NTFS drive, everything works fine except for one thing; when I try to delete a file, the system tell me that the disk doesn't have a recycle bin; so the delete will be total. How can I setup a recycle bin for this drive?
That depends on how you are mounting it in fstab. If you don't have a "uid=1000" option is fstab for that partition then the mount is owned by root. If you try to send something to your trash it tries to send it to root's trash and cannot since it's root's trash not yours.

Add "uid=1000" to your list of options in fstab just as I recommended in post #6.

---

### Post by Alex.C on 2011-08-13
> **Lupajz said:**
> Try messing with 

```
sudo apt-get install ntfs-config
```then go to : 

```
Application's-->System Tools-->NTFS configuration tool's.
```then in the window you will be able to select mounts :)

Hello, 

I've installed NTSF configuration tool, but when i go to System>Administration>NTFS configuration tool; it won't run. I'm asked to insert my login password, but after that nothing happens:(

(i'm using Ubuntu classic desktop)

---

### Post by Morbius1 on 2011-08-13
Then don't use ntfs-config. Use the method described in #6.

This is a [SOLVED] topic. It was solved using #6. If you want information on how to use ntfs-config then search the forum or start your own thread.

---

### Post by Alex.C on 2011-08-13
> **Morbius1 said:**
> Then don't use ntfs-config. Use the method described in #6.
Worked flawlessly, thanks!

---

