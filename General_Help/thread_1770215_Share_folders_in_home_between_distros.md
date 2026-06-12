---
title: "Share folders in home between distros"
date: 2011-05-28
forum: General Help
---

### Post by vehemoth on 2011-05-28
I've set up a dual boot between a few different distros that I use. One of them has a seperate home partition and I'd like to bind folders from that into the other distros' home directories, I would like to share music documents and ideally firefox bookmarks between them.

---

### Post by nzjethro on 2011-05-28
Hi there. I dual boot Ubuntu 10.10 and Win 7. I have installed each on a separate partition, and have a third partition ("Shared Files") which contains decs, music, photos, videos, downloads, etc that I want to access in both OSes.

I set up folders in my Shared partition for Docs, Pictures, Music etc, then removed the "Documents", "Music", etc folders from /home/user/. Then, I created links to the shared partition folders inside /home/user/. Then, I did the same thing in Windows (with Libraries, and the "My <docs, pictures or whatever>". Folders.

I've no experience with other Linux distros, but I imagine the process would be similar.


I used this webite:

[ http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony ]( http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony )

to set up this system. The last section may help you, in particular with setting up ntfs read/write permissions.

---

### Post by vehemoth on 2011-05-29
I think I got it sorted, I used
```

mount --bind

```

---

### Post by katykat on 2011-05-29
What file system is the shared partition on?

I have a triple boot system between XP, Meerkat, and Fedora14.

What I would like to do, and already asked in another thread (without reply) is a bit more ambitious. 

I would like to share apps between Meerkat and Fedora. I can already run apps on each other's systems, at least simple onmes - but I am wondering if anyone has ever been ambitious enough to figure a way to run the larger apps. 

For example, I dont have games on Fedora, but would like to run some of the more complex ones from Meerkat.

They would probably be needed to be run from chrooted scripts with defined paths. 

Right now Hunt the Wumpus just dont cut it.....

---

### Post by vehemoth on 2011-05-29
Well what I did was I added the following lines to /etc/fstab

```

/dev/sdb1 /mnt/sdb1 auto auto 0 0
/mnt/sdb1/vehemoth/Downloads /home/vehemoth/Downloads none bind
/mnt/sdb1/vehemoth/Music /home/vehemoth/Music none bind
/mnt/sdb1/vehemoth/Pictures /home/vehemoth/Pictures none bind
/mnt/sdb1/vehemoth/Videos /home/vehemoth/Videos none bind
/mnt/sdb1/vehemoth/Public /home/vehemoth/Public none bind

```

then ran ```
 sudo mount -a 
```
to update them

these links might help
[http://www.howforge.com/how-to-bind-directory-in-linux](http://www.howforge.com/how-to-bind-directory-in-linux)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

