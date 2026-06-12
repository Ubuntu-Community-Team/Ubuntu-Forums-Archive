---
title: "symlinking folders together - bad idea?"
date: 2009-10-26
forum: General Help
---

### Post by linuxgrrl on 2009-10-26
I have a large storage drive containing photos, videos, etc.  On my old computer I had the partitions of this drive mounted under /var/photos, /var/music, etc.

Now I am installing Ubuntu onto my new machine and learn that using /media is the preferred location for these things to be mounted.  

But my fspot and banshee databases are pointing to /var.  I have years of photos and song rankings so I plan to migrate fspot, banshee, etc., not start over.  If I make a symlink from /var/music to /media/music, /var/photos to /media/photos, etcetera, will that work?

Or is that a horrible idea for reasons I can't foresee? 

Thanks
Mary

---

### Post by jward3010 on 2009-10-26
I'd also love to hear something on this, only recently I heard about symlinking and it's pretty cool.

---

### Post by alphaniner on 2009-10-26
I would say don't be too worried about the 'preferred' method.  I mount everything under /mnt.

That said, I can't think of any problems with your proposed symlink setup.

But I'm shocked that you would be unable to make a simple change to your databases to have them point to /media.  Then again I don't know much about fspot, banshee, or databases.

Edit to add: I had forgotten, but I've used symlinks pointing directly to mount points before.

---

### Post by jward3010 on 2009-10-26
Are they literally databases or just where these programs store their libraries, for example as actual mp3's, jpegs etc.

---

### Post by linuxgrrl on 2009-10-26
Yeah, it is pretty shocking how some of those DBs are constructed.   F-spot seems to have no facility for following your photos if you ever move them.  Some die-hards have figured out how to hack mysqlite line by line in order to do it, but that seems ridiculous.  I haven't researched banshee.

One question about /var  ... when trying to get the permissions on the mounted drives set correctly, i stupidly (in a moment of desperation) changed ownership of /var and hosed my new system and had to completely reinstall.  The problem I was trying to solve (again, on the new system) was that:

ls -la /var/music showed everyone had full rwx permissions to /var/music

yet

cd /var/music gave me a "permission denied" error.

What could possibly be the reason for that?  I assume /var/music can have broader permissions that /var itself, right?

---

### Post by fuzzyllama on 2009-10-26
> **alphaniner said:**
> 

But I'm shocked that you would be unable to make a simple change to your databases to have them point to /media.  

One of the benefits of using a symlink is allowing the flexibility to move your files around as your wish without having to change programs' references to those files or their location.


A symlink is an optimal solution in this case.

---

### Post by alphaniner on 2009-10-26
Are you sure you did **ls -la /var/music**?  You know that in that case, the folder /var/music would have been indicated by '.' right?

```
testing@caddywompus:/mnt$ ls -la /mnt/bucket/
total 1527316
drwxr-xr-x 11 testing testing       4096 2009-08-24 16:00 . **<- This is /mnt/bucket**
drwxr-xr-x  7 root    root          4096 2009-09-22 16:29 ..
drwxr-xr-x  2 testing testing       4096 2009-02-04 14:13 .data
drwxr-xr-x  4 testing testing       4096 2009-05-22 14:16 Documents
drwxr-xr-x 12 testing testing       4096 2009-10-06 14:59 Downloads
drwx------  2 root    root         16384 2009-02-03 17:57 lost+found
drwxr-xr-x  7 testing testing       4096 2009-04-16 11:57 Pictures
drwxrwxrwx  6 testing testing       4096 2009-10-16 16:46 Public
-rw-r--r--  1 testing testing  536870912 2009-08-24 16:15 randjunk
drwxr-xr-x  2 testing testing       4096 2009-03-09 17:39 Templates
lrwxrwxrwx  1 testing testing          4 2009-08-20 11:50 tmp -> /tmp
drwx------  5 testing testing       4096 2009-05-22 14:16 .Trash-1000
-rw-r--r--  1 root    root    1025507328 2009-08-03 16:01 usb.dd
drwxr-xr-x  4 testing testing       4096 2009-05-22 11:03 VMs

```

Otherwise, I have no idea why you would have gotten that error.

---

### Post by fuzzyllama on 2009-10-26
> **linuxgrrl said:**
> 

What could possibly be the reason for that?  I assume /var/music can have broader permissions that /var itself, right?


your user needs -r permission for /var as well.

---

### Post by alphaniner on 2009-10-26
Good point, I didn't think of that.  However unless she did the **ls** as root, that wouldn't have worked either.

---

### Post by linuxgrrl on 2009-10-26
Yeah, I think I did "sudo ls -la /var/*" while I was troubleshooting, and it seemed to show the right permissions.

I'll try again giving read access to the parent /var directory.
Thanks!

---

