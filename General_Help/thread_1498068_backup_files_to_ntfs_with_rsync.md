---
title: "backup files to ntfs with rsync"
date: 2010-05-31
forum: General Help
---

### Post by warri0r on 2010-05-31
well, i know ther are issues when using rsync to copy files to ntfs partition like file permission blah blah. 

the thing is, i need to backup my music files periodically onto a ntfs partition from ext4. i really dont care about file permissions or any other stuff. when i use rsync, it should update the mp3 files on my ntfs (external) disc with the new ones.

the question is, can i give a go with this operation? i have lot more important files on the external disc and i dont want this rsync corrupt or delete those files coz they are highly important files. 

if no, i have to rely on manual copy paste operation. suggestion plz. thanks :)

---

### Post by warri0r on 2010-06-01
*bump* any suggestion?? :)

---

### Post by sedawk on 2010-06-01
By default rsync doesn't delete anything - in worst case
it overwrites files.

As you are only interested in copying files and do not
care about permissions I recommend to use "-r" for
recursive copy (if needed) and "--size-only" to
speed up the process. With "--size-only" rsync will
only examine the size of your music files and not
compare them byte-by-byte and it will ignore different
permissions.

E.g if you want to sync
/home/myuser/all_music with
/media/myntfs/all_music do a

```

rsync -r -v --size-only /home/myuser/all_music/ /media/myntfs/all_music/

```
or
```

rsync -r -v --size-only /home/myuser/all_music /media/myntfs/

```
In both examples the exact use of trailing slashes is important!

You can use option "-n" to do a preview before doing the
real stuff!

---

