---
title: "unable to access new data drive"
date: 2006-05-23
forum: General Help
---

### Post by bsmith1051 on 2006-05-23
I added a 2nd hard-drive to my existing Ubuntu 5.10 system.   The drive is physically connected properly and appears as 'hdb'.  After much searching, I learned that I could/should install 'gparted' as an easy way to partition it.  I created a new ext2-type partition.  I then went into System > Admin > Disks and was able to mount it as /data.  But I'm not allowed to use it?  How do I make the entire partition read-writable by regular user accounts?

Also, I did the command,
 > sudo pico /etc/fstab
and added the line,
 /dev/hdb6     /data      ext2    defaults    0    2
so that it would auto-mount.  Basically, I just copied the line for /dev/hda1 (/boot).  Should I have used different options?

Thank you for any help!

---

### Post by rralex89 on 2006-05-23
it's bacause you set the defaults options .instead of  defaults, set it to umask=0222

for example:
 
/dev/sda5       /media/sda5     ext2   umask=0222 0       0

---

### Post by rralex89 on 2006-05-23
sorry, that's umask=000 if you want read write and execute

---

### Post by bsmith1051 on 2006-05-23
[QUOTE=rralex89]umask=000 if you want read write and execute[/QUOTE]
Thanks for the hint but it still doesn't work.  The only change is that there used to be some kind of system folder visible -- and with a big red X like it was having problems -- which is no longer visible.  But it still won't let me copy any files to it.  It appears to be auto-mounting correctly at /data.

edit:  I just checked the Permissions on the '/data' folder and it's set as '754'.  Shouldn't it be '000' now?

---

### Post by aysiu on 2006-05-23
Keep your mount options the way they are in your first post.

Then paste these two commands into the terminal: ```
sudo chown -R bsmith1051:bsmith1051 /data
sudo chmod -R 755 /data
```

---

### Post by bsmith1051 on 2006-05-23
geez....

So now I went to unmount the drive but Disks Manager already showed it as unmounted.  I deleted and recreated the /data folder, but it still won't mount.

hmm, now I'm running the format command in Disks Manager.  Nope, it still shows as 'inaccessible' and won't mount.

---

### Post by bsmith1051 on 2006-05-23
[QUOTE=aysiu]Keep your mount options the way they are in your first post.
Then paste these two commands into the terminal:[/QUOTE]
Thanks, aysiu!  I think our posts crossed each other, i.e., I didn't see your response before I typed mine.

I was able to make myself the owner of the /data folder but I still can't create or paste anything into it.  I'm going to try rebooting now that I've put my 'fstab' file back to using 'default' . . . .

---

### Post by bsmith1051 on 2006-05-23
no go, I still have no access rights to the /data folder, even though it shows me as owner and has Permissions set to '755'.  But immediately after the reboot, it was listed as owned by 'root' again; I had to re-enter those 2 commands.

The system folder is back -- "lost+found" -- and it no longer has the red X.  It *did* however have the red X immediately after reboot, and the chmod command took it away.  If that's any sort of clue.

Can someone tell me the complete procedure to re-do this, maybe?  I'll delete the  mount point and the partition and just start from scratch.

---

### Post by bsmith1051 on 2006-05-23
DOH!  It just started working?  I loaded System > Admin > Disks, just to confirm that it was listed as accessible and enabled, and now it works!  I didn't change anything, though.

weird

I'd still appreciate it if someone could post a HOW-TO for the complete proper way to add an extra hard-drive.  This post has gotten spammed too much (by me)...

---

