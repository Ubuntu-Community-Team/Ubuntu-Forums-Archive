---
title: "how do I give chmod rights to another user using Root?"
date: 2011-07-18
forum: General Help
---

### Post by SkyPoweR on 2011-07-18
Hello,
I have my own 16GB sandisk cruzer flash drive,
I've already mounted him and can read on my own user,
but I can write on it only using root.
how can I give my user Chmod +x on the folder /media/XXX ?

Thanks,
Vladi.

---

### Post by cgAtom on 2011-07-18
Using this gives everyone access to the folder: sudo chmod a+rw /media/xxx

or if you want to reclaim ownership of the folder you could do sudo chown username /media/xxx

---

### Post by lisati on 2011-07-18
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SkyPoweR on 2011-07-18
mkdir: cannot create directory `/media/bigflashka/check1821': Permission denied
...

---

### Post by jocko on 2011-07-18
```
sudo chown -R $USER:$USER /media/bigflashka/
```

---

### Post by capscrew on 2011-07-18
> **SkyPoweR said:**
> mkdir: cannot create directory `/media/bigflashka/check1821': Permission denied
...

The flash drive is probably formated vFat and has no idea what chmod/chown is.  That is why it mounts as root owned.  If you want to mount the drive with your <user> name then you need to do that explicitly. See the man pages for the particulars```
man mount

*and*
 
man fstab
```

---

### Post by jocko on 2011-07-18
> **capscrew said:**
> The flash drive is probably formated vFat and has no idea what chmod/chown is.  That is why it mounts as root owned.  If you want to mount the drive with your <user> name then you need to do that explicitly. See the man pages for the particulars```
man mount

*and*
 
man fstab
```
When flash drives are auto-mounted they should automatically be owned by the current user. If that's not the case, something is wrong. You don't want to mount a removable drive through fstab.

The most likely problem I can think of is that the user is not member of the correct groups. To be able to mount a removable drive the user have to be a member of the **plugdev** group.
To check which groups the user is a member of:
```
groups
```
If the user is not already a member of the plugdev group, fix it like this:
```
sudo adduser $USER plugdev
```

---

### Post by SkyPoweR on 2011-07-18
I added a line to fstab and re-entered the flash drive..
WORKS!
SOLVED!

---

