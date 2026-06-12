---
title: "I give up, Please Help. Upgrade Drive User Permisions"
date: 2009-11-18
forum: General Help
---

### Post by isaidi on 2009-11-18
Ok here is what happened.

My 500 gig hadrive filled up, so I upgraded to 1 TB

this drive was auto-mounted to /storage  

so all i did was swap the drive to a 1 TB, and then update the fstab file with the correct UID. The drive mounts to /storage and everything is okay.


My problem begins with Transmission-daemon not able to write to the drive any more. After lots of trouble shooting, i narrowed it down to a permissions issue. But it is not on the Folder or File lever, but on the drive. 

Transmission-daemon is executed automatically using
/etc/init.d/transmission-daemon
```

!/bin/sh -e
### BEGIN INIT INFO
# Provides:          transmission-daemon
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop the transmission-daemon.
### END INIT INFO

NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=debian-transmission
# FIXME: no pidfile support; forks, so --make-pidfile doesn't work either
#PIDFILE=/var/run/$NAME.pid
STOP_TIMEOUT=3
................. 
```

Note that the user is debian-transmission.

If i change the user entry to USER = abe, then everything works fine
user abe is the main user on the machine.

here is my fstab file
```

# /home was on /dev/sda7 during installation
UUID=581750d8-d5cb-47a8-b367-c39a139c9319 /home           xfs     relatime        0       2
# /storage was on /dev/sdb1 during installation
UUID=fd4afb2c-3c1d-461a-8c35-36526b39641b /storage        xfs       relatime        0       2

```

note that /home is mounted exactly same way as /storage

Transmission is able to write sucessfully to /home drive when applying proper file permissions to the folder. However it fails to write to /storage drive, even with proper file permissions;

```

abe@oil-kube:/storage/torrents$ ls -l
drwxr-xr-x 3 debian-transmission debian-transmission 52 2009-11-17 22:47 Downloads

```

is there another location i am supposed to update drive permissions, besides the fstab file?

what's wierd is if i plug in the old drive in a USB Caddy and then change the transmission download DIR to the same location, everything works again. 

I just can't get transmission to download files to the new drive mounted on /storage using the debian-transmission user. what is wrong ?? :S :S

---

### Post by 3rdalbum on 2009-11-18
Change the permissions of the mount point to reflect what permissions you want on the drive.

(mount point is the directory that you open up to see the contents of the drive).

---

### Post by isaidi on 2009-11-18
but both /home and /storage are seperate mount-points and they have the same permissions also
```

drwxr-xr-x   4 root root    29 2009-08-23 18:47 home

drwxr-xr-x   2 root root  4096 2009-08-23 18:43 storage

```

I saw this in my /var/log/messages

```

Nov 17 23:59:53 oil-kube Thunar: Trash directory /storage/.Trash-1000 exists, but didn't pass the security checks, can't use it
Nov 17 23:59:53 oil-kube last message repeated 5 times
Nov 17 23:59:55 oil-kube xfdesktop: Trash directory /storage/.Trash-1000 exists, but didn't pass the security checks, can't use it
Nov 17 23:59:55 oil-kube last message repeated 5 times
Nov 17 23:59:55 oil-kube Thunar: Trash directory /storage/.Trash-1000 exists, but didn't pass the security checks, can't use it
Nov 17 23:59:56 oil-kube xfdesktop: Trash directory /storage/.Trash-1000 exists, but didn't pass the security checks, can't use it

```

is there a way to confirm if any of the other user acounts on my system (disabled) can access this drive?  how can i open a bash shell with the  debian-transmission user to confirm if it has access to the /storage/ drive..

from the above log, it seems like most system user accounts are not able to access the /storage drive

After mounting /storage i get

```
$ ls -l | grep storage
drwxrwxr-x   9 abe  abe    101 2009-11-17 21:23 storage

```
my downoad directory has the proper permissions too
```

$ ls -l /storage/torrents/ | grep Downloads
drwxrwxr-x 3 debian-transmission debian-transmission 52 2009-11-17 22:47 Downloads

```

---

