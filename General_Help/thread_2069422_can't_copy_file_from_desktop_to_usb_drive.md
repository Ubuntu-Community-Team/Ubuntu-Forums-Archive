---
title: "can't copy file from desktop to usb drive"
date: 2012-10-10
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-10-10
I had some sort of error (can't access my account, it rejects password when logging in).

I tried changing the password after logging into the superusers account, and it did nothing.

So, I am going to reinstall.

I did recover the necessary files by logging in as the superuser, so I have the files on the superusers desktop in a folder called 'a'. The problem is that I cannot copy that folder to a usb drive using drag and drop, the icon should show a +(plus sign) or an arrow when it is dragged to the destination drive.  And, when I drop it, nothing happens.

I tried using sudo cp to circumvent any permissions or owners issues, but it only says it can't find the folder.

Here's the terminal command I'm using:

```
sudo cp -R ~/artie/Desktop/a/  /media/377dd2ad-1b12-4aff-ae05-33738c296704
```

'a' is the folder I'm trying to copy.

'artie' is the account that is corrupted, the source of the files contained in folder 'a'.

I am logged in as the superuser (account name also 'superuser').

My usb memory stick is as follows:

```
superuser@superuser-System-Product-Name:/$ ls -l
total 96
drwxr-xr-x   2 root root  4096 Oct  8 16:01 bin
drwxr-xr-x   3 root root  4096 Oct  8 17:51 boot
drwxr-xr-x   2 root root  4096 Oct  8 13:06 cdrom
drwxr-xr-x  15 root root  4320 Oct 10 16:46 dev
drwxr-xr-x 144 root root 12288 Oct 10 16:45 etc
drwxr-xr-x   6 root root  4096 Oct 10 00:46 home
lrwxrwxrwx   1 root root    33 Oct  8 17:50 initrd.img -> /boot/initrd.img-3.2.0-31-generic
lrwxrwxrwx   1 root root    32 Oct  8 13:33 initrd.img.old -> boot/initrd.img-3.2.0-29-generic
drwxr-xr-x  24 root root  4096 Oct  8 21:46 lib
drwxr-xr-x   2 root root  4096 Oct  8 15:18 lib32
drwxr-xr-x   2 root root  4096 Oct  8 15:16 lib64
drwx------   2 root root 16384 Oct  8 13:01 lost+found
drwxr-xr-x   4 root root  4096 Oct 10 16:45 media
drwxr-xr-x   2 root root  4096 Apr 19 05:32 mnt
drwxr-xr-x   4 root root  4096 Oct  8 22:40 opt
dr-xr-xr-x 186 root root     0 Oct 10 14:46 proc
drwx------   4 root root  4096 Oct  9 15:19 root
drwxr-xr-x  20 root root   760 Oct 10 14:46 run
drwxr-xr-x   2 root root  4096 Oct  8 16:04 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 17 18:59 srv
drwxr-xr-x  13 root root     0 Oct 10 14:46 sys
drwxrwxrwt  10 root root  4096 Oct 10 17:17 tmp
drwxr-xr-x  11 root root  4096 Oct  8 15:18 usr
drwxr-xr-x  13 root root  4096 Oct 10 14:16 var
lrwxrwxrwx   1 root root    29 Oct  8 17:50 vmlinuz -> boot/vmlinuz-3.2.0-31-generic
lrwxrwxrwx   1 root root    29 Oct  8 13:33 vmlinuz.old -> boot/vmlinuz-3.2.0-29-generic
superuser@superuser-System-Product-Name:/$ cd media
superuser@superuser-System-Product-Name:/media$ ls -l
total 6
drwxrw-r-x 10 artie     artie     4096 Oct  8 12:39 377dd2ad-1b12-4aff-ae05-33738c296704
dr-xr-xr-x  1 superuser superuser 2048 Aug 17 19:16 Xubuntu 12.04.1 LTS amd64
superuser@superuser-System-Product-Name:/media$ 


```

The folder is on the superuser accounts desktop:

```

superuser@superuser-System-Product-Name:/$ cd home
superuser@superuser-System-Product-Name:/home$ cd superuser
superuser@superuser-System-Product-Name:~$ ls -l
total 32
drwxr-xr-x 5 superuser superuser 4096 Oct 10 16:14 Desktop
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Documents
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Downloads
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Music
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Pictures
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Public
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Templates
drwxr-xr-x 2 superuser superuser 4096 Oct  8 14:40 Videos
superuser@superuser-System-Product-Name:~$ cd Desktop
superuser@superuser-System-Product-Name:~/Desktop$ ls -l
total 18244
drwxrwxr-x  3 artie     artie         4096 Oct 10 16:05 a
superuser@superuser-System-Product-Name:~/Desktop$ 
```

I tried changing some permissions and some ownerships, but something is not allowing me to copy folder 'a' to my usb memory stick.

Sure would appreciate knowing what I'm doing wrong.........

TY.

Art

---

### Post by dcstar on 2012-10-11
> **goodbye-windows(tm) said:**
> 
.........
Sure would appreciate knowing what I'm doing wrong.........


You cannot copy certain Linux files to non-Linux filesystems like FAT or NTFS.

Reformat the USB device to EXT2 and try again.

---

