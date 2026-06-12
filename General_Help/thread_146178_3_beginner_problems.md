---
title: "3 beginner problems"
date: 2006-03-17
forum: General Help
---

### Post by brentlidstone on 2006-03-17
just set up ubuntu for the first time, most things running smoothly, but theres a couple things i can't figure out.
i have 3 partitions on my computer. The first is for windows XP, the second is for Ubuntu, and the third is for my documents. Working inside ubuntu, it will not let me access my windows or document partitions, giving the error "you do not have the permissions necessary..."
When I go to system>administration>users and groups it looks like it tries to start but nothing happens. I have not yet been able to open it.
I downloaded a package that ends in .deb and when I try to open it it says archive type not supported. How can I open it? Help with this and above problems greatly appreciated.

---

### Post by bluevoodoo1 on 2006-03-17
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
should help you mounting your Windows partitions (use the NTFS guide if your windows partition is NTFS, use the FAT guide if it's a FAT)

to install a .deb package, from the terminal "cd" to its folder... then to install, type
```
sudo dpkg -i thenameofyourpackage.deb
```

---

### Post by dcstar on 2006-03-17
[QUOTE=brentlidstone]just set up ubuntu for the first time, most things running smoothly, but theres a couple things i can't figure out.
i have 3 partitions on my computer. The first is for windows XP, the second is for Ubuntu, and the third is for my documents. Working inside ubuntu, it will not let me access my windows or document partitions, giving the error "you do not have the permissions necessary..."
When I go to system>administration>users and groups it looks like it tries to start but nothing happens. I have not yet been able to open it.
I downloaded a package that ends in .deb and when I try to open it it says archive type not supported. How can I open it? Help with this and above problems greatly appreciated.[/QUOTE]
Q1: Don't know 100%, but I think you have to manually modify your fstab file to allow Write access to you Windows partition - especially if it is NTFS (which Ubuntu apparently doesn't write to reliably, which is why it isn't allowed by default).

Do a forum search and I think you'll find quite a few threads on this.

Q2: This could be a root access problem, open a terminal (Right-click some vacant desktop space, select "Open Terminal") and type "sudo groups" and see what happens.

Q3: .deb files are installed with the "dpkg" command, in a terminal "dpkg --help" or "man dpkg" will give you the various options - as well as searching the forums for help.

---

### Post by brentlidstone on 2006-03-18
my terminal doesnt seem to be working either... i tried typing sudo groups and nothing happened, same with mounting my windows drive.
my internet is working though (im running it right now) and all the programs as far as I know. any ideas?

---

