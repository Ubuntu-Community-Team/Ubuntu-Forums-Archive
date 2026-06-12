---
title: "how do i add the ubuntu dvd iso as a repository?"
date: 2010-01-09
forum: General Help
---

### Post by Meow27 on 2010-01-09
so i dont feel like burning ubuntu on a dvd every 6 months, so i keep all of my images on my external harddisk.

i try mounting the dvd 9.04  image on /media/cdrom0 but it isnt recognized as a real cd-rom and wont automatically add the mounted image.

(im using gmountiso)

does anybody have a solution to this problem?

(yes im using ubuntu 9.04)

---

### Post by rnerwein on 2010-01-09
hi
just open a window --> switch to superuser and type
root@tschang:/ 22:34-> mount -o loop -t iso9660 ubuntu-9.10-desktop-amd64.iso /mnt
to unmount
umount /mnt
remember - you must run these commands with root privileges
ciao

---

### Post by Meow27 on 2010-01-09
> **rnerwein said:**
> hi
just open a window --> switch to superuser and type
root@tschang:/ 22:34-> mount -o loop -t iso9660 ubuntu-9.10-desktop-amd64.iso /mnt
to unmount
umount /mnt
remember - you must run these commands with root privileges
ciao

this doesnt solve the problem. i still cant add the disk [image] to my repository list

---

### Post by Meow27 on 2010-01-10
my original post was confusing.

everything mounts fine, but the system doesnt recognize it as a physical disk in my optical drive. (or an optical drive in general)

i seemingly need this to happen in order for the software to let me add the disk as a repository.

---

### Post by CharlesA on 2010-01-10
Are you trying to prevent it from asking for the cd when you do distro upgrades, or something else?

Ubuntu gets most everything from the repos online, not the CD (outside of the initial install).

Check here: [http://ubuntuforums.org/showthread.php?t=422588](http://ubuntuforums.org/showthread.php?t=422588)

---

### Post by michy99 on 2010-01-10
Does this help?

[http://www.zimbio.com/Linux/articles/kEIN6zMahru/Add+iso+software+repository+Ubuntu](http://www.zimbio.com/Linux/articles/kEIN6zMahru/Add+iso+software+repository+Ubuntu)

---

### Post by Meow27 on 2010-01-10
im not totally sure it worked. but i think it did. thanks

---

### Post by michy99 on 2010-01-10
If you don't get any errors when running```
sudo apt-get update
```then it probably worked.

---

