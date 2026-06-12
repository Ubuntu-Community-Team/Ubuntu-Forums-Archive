---
title: "removable drive permissions - how do you actually configure them?"
date: 2009-10-15
forum: General Help
---

### Post by inspiteofmyself on 2009-10-15
to start with, ill say this flat out because it is the solution given to every thread and discussion i have seen this question asked in.

no i do not want to add my removable devices to /etc/fstab. if that was your solution, or you were going to show me a thread where that solution was offered, spare us the clutter and lets actually figure this out ;)

by default, mpd is installed to change to a user named 'mpd'.

if your music directory is set to a removable device, and the device is plugged in as say a user named 'bob' you get the following when starting mpd.

```

 * Starting Music Player Daemon mpd                                             failed to stat music directory "/media/Music/Music" (config line 8): Permission denied

```

if i change the mpd user to "bob" in /etc/mpd.conf, and then change ownership of /var/log/mpd and /var/run/mpd to bob:bob...mpd runs fine, and works fine.

this is also an undesirable fix though. i want my mpd to be run by 'mpd' as it is installed to do.

i have tried writing a policy to mount the drive with permissions for everyone, it did not work no matter how i tried to make it work. the drive was always mounted as being owned and readable only to the user logged into the current console when the device was connected.

the results of cat /proc/mounts shows the following:

```

/dev/sde1 /media/Music fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0

```

is there some group i can add mpd to that will allow him to use that mount? is there some way to actually make a policy that will make the drive mount as at least readable by other users?

---

