---
title: "Unable to move Home directory"
date: 2010-12-28
forum: General Help
---

### Post by JeepFreak on 2010-12-28
Ubuntu 10.10 32 bit

*/* and */storage* are on two different partitions.  I want to move my home directory to the */storage* partition, so I went to **System** -> **Administration** -> **Users and Groups** then **Advanced Settings** then the **Advanced** tab.  I changed **Home Directory** from */home/billy* to */storage/home/billy*.  I click on **ok** and I'm asked if I want to copy all the user's files over to the new location or start fresh.  I click, **Copy Files**.  It acts like it's doing something, but all it does is create the *home/billy* directories inside */storage*, but it never copies files over and the next time I go to /home/billy it's still in the old location.  What the heck is the deal?

Any help is really appreciated!  I couldn't find anything here or Google that would help.

Thanks again,
Billy

---

### Post by K.J. on 2010-12-28
First try this:
sudo usermod -d /path/to/new/home -m

If that doesn't do the trick--

Create the folder on the partition you want and set up the correct permissions:
```
mkdir /path/to/new/home
chown yourusername /path/to/new/home
chmod 644 /path/to/new/home
```

Next you'll want to copy your existing home over while preserving permissions:
```
cd /home
sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /path/to/new/home
```

Finally you'll want to change the home path to new directory:
```
sudo mv -R /home /home_old
sudo ln -s /path/to/new/home /home
```

Reboot, if all went well you can delete the old home:
```
sudo rm -R /home_old
```

If your home folder is the only thing on that partition, you can mount the hard drive directly to home and skip the last step.

---

### Post by JeepFreak on 2010-12-28
> **K.J. said:**
> First try this:
sudo usermod -d /path/to/new/home -m

If that doesn't do the trick--

Create the folder on the partition you want and set up the correct permissions:
```
mkdir /path/to/new/home
chown yourusername /path/to/new/home
chmod 644 /path/to/new/home
```

Next you'll want to copy your existing home over while preserving permissions:
```
cd /home
sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /path/to/new/home
```

Finally you'll want to change the home path to new directory:
```
sudo mv -R /home /home_old
sudo ln -s /path/to/new/home /home
```

Reboot, if all went well you can delete the old home:
```
sudo rm -R /home_old
```

If your home folder is the only thing on that partition, you can mount the hard drive directly to home and skip the last step.

Thanks for the response K.J.  Just to be clear, when you reference "home" above, are you really talking about "home" (where all users' home folders are stored) or "home/billy" (my individual home folder)?  I am the only user (as of right now), but obviously there's a difference.

Thanks again!
Billy

---

### Post by K.J. on 2010-12-28
When I say home, I mean the /home folder and not /home/username. I suggest moving the entire home folder and not just one user's directory, although it is possible to do that with a linked folder.

---

### Post by gmargo on 2010-12-28
> **K.J. said:**
> 
```

sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /path/to/new/home
```

You'll need to add a "-m" to the **cpio** options to preserve modification time. Personally, I prefer to leave out the "-v" verbose flag so that any errors are obvious.  Otherwise very good advice.

---

### Post by JeepFreak on 2010-12-28
OK, so the "mv -R" didn't work, but upon researching it, it seems that it's because "mv" is, by default, reclusive, so I left off the "-R".  I also added in the "-m" that gmargo suggested.

I also, apparently, screwed something else up too because I now have /home/home/billy and, of course, ubuntu isn't loading correctly.  I tried fixing it but I'm getting all kinds of permissions errors and such.

Any way you guys can help me reverse what I did and fix it?

I would really appreciate it.
Thanks,
Billy

---

### Post by xyepblra on 2010-12-29
Guys, I'm going to move my /home previously located on an ext4 partition to a bigger partition. I'm going to use an instruction provided by K.J., and would like to avoid repeating what JeepFreak did, so could somebody please revise the instruction provided by K. J.?

---

### Post by dcstar on 2010-12-29
> **xyepblra said:**
> Guys, I'm going to move my /home previously located on an ext4 partition to a bigger partition. I'm going to use an instruction provided by K.J., and would like to avoid repeating what JeepFreak did, so could somebody please revise the instruction provided by K. J.?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

