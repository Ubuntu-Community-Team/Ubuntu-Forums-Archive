---
title: "Folder/File Ownership."
date: 2010-06-30
forum: General Help
---

### Post by warfacegod on 2010-06-30
I need to know how to change the ownership of a folder and everything within it through the Terminal. chown, in this case, isn't going to work. Thanks in advance.

---

### Post by justleen on 2010-06-30
Why wouldn't chown/chmod work?

---

### Post by warfacegod on 2010-06-30
chown won't work because it's the /home partition.

---

### Post by justleen on 2010-06-30
sudo chown?

What do you need changed then? 
perhaps a find -exec chmod {} \;   can help?

---

### Post by vanadium on 2010-06-30
It will have to be chown. With -R you specify it should affect all subfolders, and finally, you provide the name of the folder concerned.

sudo chown -R someone:somegroup /home/someone/directory_to_change

---

### Post by warfacegod on 2010-06-30
Even sudo chown. Well, perhaps I'm wrong. I assumed that chown was for entire partitions and drives evidently I am mistaken.

Within the /home partition one of the users files are almost all owned by root not that user. This, of course, makes Ubuntu rather difficult to use. Panel won't load, etc. I need to change the ownership of those folders and files only. If I simply chown the /home, I'll change ownership of *all* files to that user. I'll have 3 users that can't use their account and 1 that can instead of it being the other way around as it is now.

---

### Post by Leppie on 2010-06-30
yes, i agree. use sudo chown:
```
sudo chown warfacegod:warfacegod /home
```

though this would seem to be counterproductive...
or if you want to set your own group as the group owner:
```
sudo chown root:warfacegod /home
```

as vanadium said, -R will set all the sub folders and files with he same ownerships (and that really is counterproductive).

---

### Post by warfacegod on 2010-06-30
> **vanadium said:**
> It will have to be chown. With -R you specify it should affect all subfolders, and finally, you provide the name of the folder concerned.

sudo chown -R someone:somegroup /home/someone/directory_to_change

You know, in hind sight, that's quite obvious. I keep a file of Terminal Commands and my chown entry looks like this:

```
sudo chown -R username:usergroup /media/drivename
```

It never occurred to change the path.

---

### Post by justleen on 2010-06-30
If you want to set proper permissions for the user, then don't apply permission recursivly on /home.

chown -R user:user /home/user

That way your sure everything in the users folder is actually owned by that user...

---

### Post by Leppie on 2010-06-30
> **warfacegod said:**
> Even sudo chown. Well, perhaps I'm wrong. I assumed that chown was for entire partitions and drives evidently I am mistaken.

Within the /home partition one of the users files are almost all owned by root not that user. This, of course, makes Ubuntu rather difficult to use. Panel won't load, etc. I need to change the ownership of those folders and files only. If I simply chown the /home, I'll change ownership of *all* files to that user. I'll have 3 users that can't use their account and 1 that can instead of it being the other way around as it is now.
then use it like this:
```
sudo chown -R <username>:<username> /home/<username>
```

---

### Post by warfacegod on 2010-06-30
> **Leppie said:**
> yes, i agree. use sudo chown:
```
sudo chown warfacegod:warfacegod /home
```

though this would seem to be counterproductive...
or if you want to set your own group as the group owner:
```
sudo chown root:warfacegod /home
```

as vanadium said, -R will set all the sub folders and files with he same ownerships (and that really is counterproductive).

This isn't my computer. There's no way I'd allow some dumb crap like this happen to my own equipment. Anyway, why would this be counter productive? If virtually everything in the users folder is owned by root, personal and settings both, I would think changing the ownership back would get everything back to normal. I've been poking around in the hidden folders/files in my Home, to compare, and it looks like I own everything.

---

### Post by justleen on 2010-06-30
doing chown for 1 user on the whole /home/ is counterprodcutive, since you effectivly revoke 2 of the 3 users rights...

---

### Post by Leppie on 2010-06-30
> **warfacegod said:**
> This isn't my computer. There's no way I'd allow some dumb crap like this happen to my own equipment. Anyway, why would this be counter productive? If virtually everything in the users folder is owned by root, personal and settings both, I would think changing the ownership back would get everything back to normal. I've been poking around in the hidden folders/files in my Home, to compare, and it looks like I own everything.
yes, i had not seen your other post yet.
but usually if you don't play around with the permissions too much, a user's whole home would not be owned by the root user and group ;)

---

### Post by warfacegod on 2010-06-30
Someone handed me their computer with a backup of each users Home. After doing a fresh install, I discovered that the Desktop users simply drag n' dropped their Home. Fine. The Admin. user, on the other hand, moved her Home as root. Doh!

Anyway, problem solved.

This worked nicely:

```
sudo chown -R <username>:<username> /home/<username>
```

Thank you, everyone, for pointing out that I need to be more diligent about drinking coffee *before* I start working on a computer. I really should have seen this myself.

---

### Post by Leppie on 2010-06-30
> **warfacegod said:**
> Thank you, everyone, for pointing out that I need to be more diligent about drinking coffee *before* I start working on a computer. I really should have seen this myself.
you should be more diligent about drinking coffee before starting *anything*... :lolflag:

anyways, glad it worked.

---

