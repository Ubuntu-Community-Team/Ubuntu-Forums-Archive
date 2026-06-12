---
title: "Backup to network drive"
date: 2012-01-12
forum: General Help
---

### Post by garfieldpbj on 2012-01-12
Hi

I do primarily use a notebook with ubuntu installed on it. 

I have an "server" computer, actually just a computer not normally used, with a hard drive suitable for backup via the network.

I want to "manually" backup once a month by executing some script.

I have searched through the forum (and WWW in general), and found many solutions.

What do you recommend me to do? 

I have approx. 40 GB of data which I want to back up - because of this I think something with rsync, or some other tools, only backing up changed files is preferred.

What would you recommend?

/Peter

---

### Post by zero2xiii on 2012-01-12
Haya,

Yes, rsync will be the solution that is most easy to use and or script.

Hit the rsync man page for the details on flags to only update changes files

Just make sure about the write access you have to the drive.. Thats usualy where the biggest hicups come in.
Cherz

---

### Post by garfieldpbj on 2012-01-12
> **zero2xiii said:**
> 
Just make sure about the write access you have to the drive.. Thats usualy where the biggest hicups come in.
Cherz
What do you mean? The available speed or what? 

I would probably connect via wlan (or ethernet if to slow) to the backup server.

/Peter

---

### Post by zero2xiii on 2012-01-12
Hay,

All it means, since the drive you will be backuping to, will be over a network. You have to make sure the pc you are backing up, are able to write to the network source first.

Cherz

---

### Post by Double.J on 2012-01-12
Hi there, not sure if I recommend - as you say there are so many options for data protection - but I use dd. My drive has 5 OS on it so I like to use complete hard drive imaging as my back up technique for the OS's once a fortnight or so, and bzip to compress my shared data once a week then copy the archive over to the backup drive. TBH I usually do this graphically unless I happen to be working in the terminal, but I rarely am on a Sunday!

for the complete hard drive imaging I use a slightly shortened version of the following commands from a live environment

```

dd if=/dev/sda conv=sync,noerror bs=64 of=/path/to/new/hdd/image.img 
tar cjfv newharddriveimg.img.tar.bz2 /path/to/image

```

I also keep a copy of my hard drive image on online storage. Most have upload file size limits, so I use split to cut it up into bits for uploading :)

Mines a very complicated and time consuming way to back up - but It does result in a complete hard drive image that's never more than a month old and stored away from my machine.. as I say I'm the first to admit it's not a back up strategy for everyone, and I definately wouldn't recommend running the dd command across a wirless connection!

---

### Post by garfieldpbj on 2012-01-12
> **zero2xiii said:**
> Hay,

All it means, since the drive you will be backuping to, will be over a network. You have to make sure the pc you are backing up, are able to write to the network source first.

Cherz

I can do whatever I want to both drives :-) Both via network and login in physically at the computers, because I am admin!

---

### Post by garfieldpbj on 2012-01-12
> **gnu/mirow said:**
> 
Mines a very complicated and time consuming way to back up - but It does result in a complete hard drive image that's never more than a month old and stored away from my machine.. as I say I'm the first to admit it's not a back up strategy for everyone, and I definately wouldn't recommend running the dd command across a wirless connection!

I agree - very time consuming :-( 

Because I am probably only changing or adding 1 or 2 gb of data (out of the ~40 gb), I think a "syncing" backup is preferred, therefore I will not follow your suggestions - but thanks anyway :-)

/Peter

---

### Post by zero2xiii on 2012-01-12
> I can do whatever I want to both drives  Both via network and login in physically at the computers, because I am admin!
> Because I am probably only changing or adding 1 or 2 gb of data (out of the ~40 gb), I think a "syncing" backup is preferred

Awsome :)

Here you go:
Change <PATH_BACKUP_FROM> to the path you want to backup (sync)
Change <PATH_BACKUP_TO> to the path you want to backup to (sync)

```
rsync -ru <PATH_BACKUP_FROM> <PATH_BACKUP_TO>
```
-r is recursive.
-u is for update files.

This should work. For a more task specific design, please see the man page:
```
man rsync
```

Cherz

---

### Post by garfieldpbj on 2012-01-12
> **zero2xiii said:**
> Awsome :)

Here you go:
Change <PATH_BACKUP_FROM> to the path you want to backup (sync)
Change <PATH_BACKUP_TO> to the path you want to backup to (sync)

```
rsync -ru <PATH_BACKUP_FROM> <PATH_BACKUP_TO>
```
-r is recursive.
-u is for update files.

This should work. For a more task specific design, please see the man page:
```
man rsync
```

Cherz

Thank you, I will probably try the rsync if I do not get any other (better) suggestion :-)

Thanks :-)

---

### Post by CharlesA on 2012-01-12
+1 to rsync from me. That's what I use.

---

