---
title: "Sharing and Permissions"
date: 2010-07-24
forum: General Help
---

### Post by vandorjw on 2010-07-24
Hey Everyone,

I have 4 hard-drives in my tower.
Hard-drive 1 contains all the system files.
hdd 2 contains all music
hdd 3 contains video
hdd 4 contains misc data

The root of the system "/" is on drive 1, and I used fstab to mount hdd 2 - 4 under /storage/music /storage/video and /storage/misc

I want /storage/misc to be readable and writable by people on the LAN.
The other 2, I would like to be "read" only

My question is, what should I set the permission of /storage to and what should i put /storage/misc to.

If I put /storage/misc to 777 (chmod 777 -R /storage/misc), will people ever be able to go up the "tree" and ever get access to "/"?

I hope my question makes sense. If there is a good article somewhere that explains it nicely, just provide the link :)

Cheers - CC7

---

### Post by geoffjay on 2010-07-24
Better to use ugo+rwx than 777, it sounds like what you want is

chmod u+rw -R /storage
chmod go-rwx /storage
chmod g+rw -R /storage/misc

If you've already set 777 on everything in those directories you've effectively made every file executable, you probably don't want this. To fix that you could do this, but I'll warn first that if you've got executables in these directories that need the x bit set this is going to undo that.

find /storage -type d -exec chmod 755 -f {} \;
find /storage -type f -exec chmod 644 -f {} \;

edit: I probably should have explained the ugo part, u - user, g - group, o - other.

---

### Post by vandorjw on 2010-07-25
ugo = user group other right?
Last night I did bunch of research and came across some helpful sites. Will post them later.

thanks,

cc7

---

