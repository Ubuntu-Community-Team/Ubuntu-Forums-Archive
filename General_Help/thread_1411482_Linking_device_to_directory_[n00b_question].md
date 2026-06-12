---
title: "Linking device to directory [n00b question]"
date: 2010-02-20
forum: General Help
---

### Post by Neonlights on 2010-02-20
Okay I have mounted "sdb" to "/storage"
I would like to create a shortcut to "/storage" in "/var/www/web"
I know i cant use "ln -d" because of hard linking across devices. but "ln -s" say "no such file or directory".
 
Is there a way I can do this?
 
P.S. - I'm using all command line and no GUI.

---

### Post by Neonlights on 2010-02-20
bump

---

### Post by SuperSonic4 on 2010-02-20
What is the output of ```
ls -l /var/www/web
```

I tried a symlink from /media/Pictures to /var/Picutre (because my spelling sucks)

```
[13:32:23]ln -s /media/Pictures/ /var/Picutre
```

```
ls -l /var/Picutre
lrwxrwxrwx 1 root root 16 Feb 20 13:33 /var/Picutre -> /media/Pictures/
```

When I navigate in dolphin the symlink works.

I should add /media/Pictures is on sda but my OS is on sdb

---

### Post by rnerwein on 2010-02-20
hi 
my be this will help you:
if have mounted an usb-stick on /media --> /dev/sdb on /media/USB_2GB type vfat ........
in my home directory i have a directory: --> ~/usb2gb
and using: mount /dev/sdb /home/xyz/usb2gb

and the result is: --> /dev/sdb on /media/USB_2GB type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

---> /dev/sdb on /home/xyz/usb2gb type vfat (rw)

also i got another automount option in my fstab:
/dev/sda7 /suse_data ext3 defaults,suid,noauto                0    0
# to share directories 
/suse_data/xyz /suse_xyz/xyz_shared auto,none bind
where suse_data/xyz is my home directory of suse-linux

ciao

---

### Post by mcduck on 2010-02-20
> **Neonlights said:**
> Okay I have mounted "sdb" to "/storage"
I would like to create a shortcut to "/storage" in "/var/www/web"
I know i cant use "ln -d" because of hard linking across devices. but "ln -s" say "no such file or directory".
 
Is there a way I can do this?
 
P.S. - I'm using all command line and no GUI.

Symbolic links (ln -s) should work just fine. Could you give the exact command you tried to run?

("no such file or directory"-error sound like you just mistyped the source or destination path...)

---

### Post by oldfred on 2010-02-20
When I link it is to a folder in the data directory.

Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

I also had to give myself permissions and ownership:
   72  sudo chown fred:fred /usr/local/fred
   47  sudo chmod 766 /usr/local/fred/data

# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents

---

### Post by Neonlights on 2010-02-20
ln -s storage /var/www/web
 
I get one of two errors
 
1. No such file or directory
2. Too many levels of symbolic links
 
 
NOTE: I'm not trying to mount the drive to this location (because I would like it mounted in the home directory). I would just like to make a link to the mount point, so I can access it from the internet.

---

### Post by Neonlights on 2010-02-20
Issue has been solved.
 
when creating the symbolic link, due to my device being mounted under my home directory I was required to put the full source /home/user/storage to create the link no just /storage.
 
so for the future
 
ln -s /home/user/storage /var/www/web
 
not
 
ln -s /storage /var/www/web

---

### Post by SuperSonic4 on 2010-02-20
That is because / is the root heirachy. If you were in ~ then you could have just put storage.

ln was trying to look in the top level instead of where storage was

---

