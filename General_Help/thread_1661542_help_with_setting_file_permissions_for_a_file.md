---
title: "help with setting file permissions for a file"
date: 2011-01-06
forum: General Help
---

### Post by luke0927 on 2011-01-06
Hopefully someone can help me I have system at work I am setting up that runs on linux, it was powered up back in september but we didn't get the details to configure until this week, unfortunatly var filled up with 100% spaced used due to a log file that keeps being written to until its intizilized, I can't just delete the file so (will not be recreated), I pulled it off and took it home and split it into a smaller file (from 740mb down to a 15mb chunk)I'm really just a linux newbie so can someone explain to me what the permissions are on the current file and then what chmod would make smaller file the same  Thanks!

clusternet.log is the orginal and clusternet1.log is the one i made from split.

I know its read, write and execute (whats the r write after x on clusternet.log?) but I'm not sure on what it means in the position its in, the clusternet.log should have permissions only for root correct?


```
-rw-r--r--  1 luke luke  16613376 2011-01-06 20:10 clusternet1.log
-rwxr-----  1 luke luke 740130816 2011-01-06 06:39 clusternet.log
```

---

### Post by efflandt on 2011-01-06
Permissions start with d for dir or - for a file in the 1st slot

Next 3 permissions are for **user who owns it** (luke in this case), so rwx means that, but execute (x) would be **very unusual** for a log file which at most would be read/write (ie, rw-)

Next 3 permissions are for **group** (group luke in this case), in which case r-- means that group luke has read permission.

Next 3 permissions are for **others**, meaning anyone not the specified user or group (--- means no permissions for others).

But was clusternet.log really owned by luke originally, or was it owned by root or some other system user and group?

If a 740 MB file chokes /var, it sounds like your /var is too small.  And you should probably configure it with log rotation that regularly rotates, compresses, and removes old logs (like other files in /var/log).

---

### Post by luke0927 on 2011-01-06
> **efflandt said:**
> Permissions start with d for dir or - for a file in the 1st slot

Next 3 permissions are for **user who owns it** (luke in this case), so rwx means that, but execute (x) would be **very unusual** for a log file which at most would be read/write (ie, rw-)

Next 3 permissions are for **group** (group luke in this case), in which case r-- means that group luke has read permission.

Next 3 permissions are for **others**, meaning anyone not the specified user or group (--- means no permissions for others).

But was clusternet.log really owned by luke originally, or was it owned by root or some other system user and group?

If a 740 MB file chokes /var, it sounds like your /var is too small.  And you should probably configure it with log rotation that regularly rotates, compresses, and removes old logs (like other files in /var/log).

Thanks I can't make any changes to the system I just need to initialize and put code and IP's this is all preconfigured stuff so can't make any changes its just a small drive to hold the internal settings and once I kick off a command called FPclusternetlog it will allow me to initialize the network but basically its just been sitting there saying discoverd switches etc...over and over because it wasn't init'd 

I had to be root on the system to do anything with that file, I'm hoping I can make the file I created the same permissions remove the other file and put it in its place and kick off my script that sets the network up. I completly removed it and it will not work or recreate the file. so what would be the prober chmod command to set the permission to where only root user can access the file?

This isn't really a system I specialize in, so I may have to go to support but was trying to get it on my own first. I'm more of a SAN guy.

here is what it is

[http://www.emc.com/products/family/emc-centera-family.htm](http://www.emc.com/products/family/emc-centera-family.htm)

---

### Post by luke0927 on 2011-01-06
I got it figured out set it 700 then added g+r, well see if it works.

---

