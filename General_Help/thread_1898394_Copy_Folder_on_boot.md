---
title: "Copy Folder on boot"
date: 2011-12-21
forum: General Help
---

### Post by pbeesley on 2011-12-21
Quick background: I dual boot

Longer background and request: I dual boot with windows (for games) and would like to take a backup of my windows save files to my ubuntu one folder everytime I boot into ubuntu.

in my head I can just created a script that looks like this

```
sleep 60 (to allow drives to mount)
&&
cp /media/WINDOWS/docs/MY_SAVE_GAMES /UBUNTU/home/ubuntu_one

```

is it that simple or am I missing something?

---

### Post by Lars Noodén on 2011-12-21
It's that simple.  You could also use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) so that only changes get copied.  It would save bandwidth if the files are large or many.

```

rsync -a /media/WINDOWS/docs/MY_SAVE_GAMES /UBUNTU/home/ubuntu_one/

```

To have it happen when you boot up, put it in [font=Courier New]/etc/rc.local[/font]

---

### Post by pbeesley on 2011-12-23
Perfect JUST what I wanted :popcorn:

---

