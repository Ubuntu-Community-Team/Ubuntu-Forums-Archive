---
title: "NTFS configuration tool won't start"
date: 2009-07-03
forum: General Help
---

### Post by TheHimself on 2009-07-03
I've installed NTFS configuration tool to be able to mount an NTFS partition automatically but when I run it it gives a "segmentation fault" error and terminates. What should I do?

---

### Post by blueridgedog on 2009-07-03
I can show you how to mount the partition by hand, but there is a bit of terminal work to it.  If you are up to it, post the output of the command:

```
sudo fdisk -l
```

So I can see where the partition is you want to mount.

---

### Post by TheHimself on 2009-07-04
I know how to mount it "by hand". ```
sudo mount /dev/sda7
```
I'd like it to be mounted automatically at boot time. I put the command above in the "Startup Applications" but it doesn't work.

---

### Post by blueridgedog on 2009-07-04
I meant by hand so that it mounts automatically.

In the following substitute you user name for USER.  Change the name of the mount point to suit you, just replace it everywhere so that the commands are consistent.

Make a directory for the drive to be mounted to:

```
mkdir /home/USER/files
```

Unmount the drive from its existing mount point:

```
sudo umount /dev/sda7
```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep USER
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit /ect/fstab to mount the drives in the new locations
```

gksudo gedit /etc/fstab
```

Add The following line:

```
/dev/sda7 /home/USER/files ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1

```

Save the file then mount the drive with
```

sudo mount /home/USER/files

```

Remember to change USER everywhere you see it and also you can adjust the mount point as you want, but make certain you own the mount point.  If you make a mount point in another part of the system, give yourself ownership with:

```
sudo chown USER:USER /path/to/new/mountpoint
```

With the entry in /etc/fstab, it will mount when you boot.

---

### Post by TheHimself on 2009-07-06
Thanks for the detailed info. Isn't it possible to have it mounted as before in   /media/E ?  I'm afraid my Nautilus bookmarks (in E) might stop to work.

---

### Post by blueridgedog on 2009-07-06
> **TheHimself said:**
> Thanks for the detailed info. Isn't it possible to have it mounted as before in   /media/E ?  I'm afraid my Nautilus bookmarks (in E) might stop to work.

Yes, just substitute /media/E for the mount point.  The instructions are generic in case a user wants to mount it in a custom location.

---

### Post by riglo on 2011-10-09
i had the same problem : after downloading just type 
[FONT=Calibri][SIZE=3]**sudo apt-get upgrade ntfs-config **[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]this should upgrade and you should be able to run the config tool[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]

---

### Post by drs305 on 2011-10-09
> **TheHimself said:**
> I'd like it to be mounted automatically at boot time. I put the command above in the "Startup Applications" but it doesn't work.

Just for future reference: Startup Applications is controlled by each user and is not run as root. Since your command is using a 'sudo' command, it isn't going to allow it to run unless you edit some of your system files to accommodate it or run it in a way which will ask you for the password after booting. If you look in /var/log/auth.log you can find the error

To run commands requiring root privileges at startup, you would place the commands in one of the /etc/init.d files - such as rc.local.

---

