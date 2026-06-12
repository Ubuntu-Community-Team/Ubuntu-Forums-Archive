---
title: "Perminently Mount Drive"
date: 2009-11-07
forum: General Help
---

### Post by nexoncore on 2009-11-07
How would I go about editing by ubuntu installation to keep a mounted drive perminently mounted.

**Scenario**
Computer has 2 hard drives. One HDD holds both Windows and Ubuntu, second one holds all of the files I access from both OS, including music library, movies, images, documents.

Problem is, since ubuntu no longer has Remember Authentication option, every time I start songbird, I need to remount the HDD2.

[B]Summary
[/B]Ideally I would like to make it so ubuntu either perminently mounts the second hard drive on boot. Or that if a mounted HDD is not unmounted before shutting down, it keeps it mounted the next time ubuntu is started.

---

### Post by ivanvajar on 2009-11-07
What Ubuntu are we talking about? 9.10?

---

### Post by ivanvajar on 2009-11-07
Did you try program called 'pysdm'?

---

### Post by Olav on 2009-11-07
You need to edit your /etc/fstab. I can't give you the exact line you need to add, because it will depend on your system. It may end up looking like this:

/dev/sdb1 /media/hdd2 ntfs-3g defaults 0 0

Search this forum for "fstab" and I am sure you will find more information.

---

### Post by ivanvajar on 2009-11-07
Try [here]("http://superuser.com/questions/62483/automount-in-ubuntu-9-10")

---

### Post by nexoncore on 2009-11-07
I tried pysdm, but when I open the program, all options are disabled and it wont do a thing, so I am trying the other suggestions now.

---

### Post by vsperez on 2009-11-07
Just like Olav said. You can edit /etc/fstab and add a  line like this:

/dev/sda2    /path/to/myWinPartition    ntfs  defaults 0 0

You will get it mount on start-up.

---

### Post by efflandt on 2009-11-07
Whatever you do, you have to sudo (or gksudo in gnome), because it has to be done as root.  For example: **gksudo gedit /etc/fstab**

See **man fstab** which may seem sort of cryptic if unfamiliar with it, but looking at the fstab file may make things clearer.  Whitespace between fields can be any number of spaces or tabs.  You can use /dev/sdb# or whatever it is instead of UUID.  The directory you mount it on has to exist (**sudo mkdir** /path if you need to create it).

---

### Post by nexoncore on 2009-11-07
I ended using NTFS configuration utility, which did the job perfectly. Thanks for you help

---

