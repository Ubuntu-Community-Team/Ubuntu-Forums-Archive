---
title: "Laptop Died During 9.04 -&gt; 9.10 dist-upgrade!"
date: 2009-11-09
forum: General Help
---

### Post by doggbat on 2009-11-09
Well, the title says most of it.

When I boot my laptop, I get "One or more of the mounts listed in /etc/fstab cannot yet be mounted".

I tried following instructions to
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

sudo apt-get update will not run.. It says to run sudo dpkg --configure -a.

When I do sudo dpkg --configure -a, I am told that dpkg could not get a lock and that my filesystem is read-only.

I tried sudo mount -o remount,rw /dev/sda1 , but this just told me that /dev/sda1 was not yet mounted.

I am completely clueless as to what to do (as you can probably see, I don't have a lot of knowledge in this area).  Any help would be greatly appreciated.

---

### Post by doggbat on 2009-11-09
I ran
```
sudo mount /dev/sda1 /
```

It replied

```
mount: /dev/sda1 already mounted or / busy
mount: according to mtab, /dev/sda1 is already mounted on /
```

---

### Post by doggbat on 2009-11-09
I deleted /var/lib/dpkg/lock and ran
```
sudo dpkg --configure -a
```
Response:
```
dpkg: unable to access dpkg status area: Read-only file system
```
so it got rid of the stuff about not getting the lock...

---

### Post by jeb800e on 2009-11-09
Best fix: Reformat your hard drive and completely re-install Ubuntu from the ground-up using the Live CD

---

### Post by doggbat on 2009-11-09
Yeah, I was trying to find a way around that.. But I guess I'm giving up and reinstalling.

---

