---
title: "Changing the /home directory (n00b question)"
date: 2009-09-28
forum: General Help
---

### Post by bravo sierra echo on 2009-09-28
Hopefully anyone who knows KDE well can help me...

I have Kubuntu Jaunty Jackalope installed.  I've bought a new hard drive, and my plan is to keep the install I have and use the new HD as a storage drive.  This will make life easier if I want to re-install, or use a different OS.

I therefore want /home to point to the new drive, so that users' files appear there.

I know this can be done during installation (because I've set up Xubuntu on another machine this way) but I can't figure out how to change it on an already-installed system!

---

### Post by Giblet5 on 2009-09-28
The home directory is defined by the /etc/passwd file.

```
sudo gedit /etc/passwd
```

The file's format is defined in section 5 ```
man 5 passwd
```
Just change the home directory in that file.

Example:
bobbilly has a home directory in /home/bobilly

The /etc/passwd file has:
bobbilly:x:1011:1011:William Bob:/home/bobbilly:/bin/bash

Change the home to /samba/monkeymen/bob.

Then create, copy his original files, and set ownership on that directory:
```
sudo bash
cd /home/bobbilly
mkdir /samba/monkeymen/bob
chown bobbilly:bobbilly /samba/monkeymen/bob
chmod 750 /samba/monkeymen/bob
tar cf - . | (cd /samba/monkeymen/bob;tar xf -)
cd /home
rm -fr bobbilly
exit
```

---

### Post by Giblet5 on 2009-09-28
It's worth pointing out that the "standard" is to use /home for home directories. There are sometimes reasons for changing that, but they're not often Good reasons.

---

### Post by openfly on 2009-09-28
might also be changeable via chsh.

---

### Post by imbjr on 2009-09-28
Isn't this also do-able by having /etc/fstab mount the new hard-drive at /home/<you>?

---

### Post by i.r.id10t on 2009-09-28
> **imbjr said:**
> Isn't this also do-able by having /etc/fstab mount the new hard-drive at /home/<you>?

Correct... well, actually, you want to mount /home in general on the new drive.

You can use blkid to get the UUID for the drive you want to use as /home

Boot with a live cd or don't log in and go to a virtual terminal, mount the new drive someplace like /home-new, copy all the files/directories from /home, rename /home to /home-old, then unmount the drive and re-mount it at /home

---

### Post by Giblet5 on 2009-09-28
> **imbjr said:**
> Isn't this also do-able by having /etc/fstab mount the new hard-drive at /home/<you>?

That will change ALL users.

Bravo said A user.

That's probably what s/he wants though.

---

### Post by imbjr on 2009-09-28
> **Giblet5 said:**
> That will change ALL users.

No, I said /home/<you>, so only the user <you> would be affected.

---

