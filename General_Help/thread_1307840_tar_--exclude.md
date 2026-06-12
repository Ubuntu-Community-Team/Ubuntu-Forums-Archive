---
title: "tar --exclude"
date: 2009-10-31
forum: General Help
---

### Post by jesuisbenjamin on 2009-10-31
Hi there!

I would like to compress and back up my home folder excluding /Music and /Pictures which i have saved separately on DVD.

Now i puzzled with tar and the --exclude= argument but --exclude=/Music did not prevent tar from including the /Music folder...

What ought to be done in this case?

Thanks.

---

### Post by ibuclaw on 2009-10-31
> **jesuisbenjamin said:**
> Hi there!

I would like to compress and back up my home folder excluding /Music and /Pictures which i have saved separately on DVD.

Now i puzzled with tar and the --exclude= argument but --exclude=/Music did not prevent tar from including the /Music folder...

What ought to be done in this case?

Thanks.

Shouldn't it be:
```
--exclude=~/Music
```
?

Regards
Iain

---

### Post by jesuisbenjamin on 2009-10-31
I tried --exclude=~/Music as well but it didn't work:

```
benjamin@buddhi:/home$ tar cjvf /media/OS/benjamin_backup.tar.bz2 benjamin --exclude=~/Music --exclude=~/Pictures

benjamin/
benjamin/vlc/
benjamin/vlc/ASkin.vlt
benjamin/.gtk-bookmarks
benjamin/.dbus/
benjamin/.dbus/session-bus/
benjamin/.dbus/session-bus/dfb97b07441b91ce3fd610cc491dc7b8-0
benjamin/Music/


etc...
```

---

### Post by lilbill on 2009-10-31
I always use
```

tar options --exclude "/full/path/to/directory"

```
Seems to work for me.  Using the absolute path eliminates ambiguities.

---

### Post by phillw on 2009-10-31
This thread has good explain of tar, and backing up stuff.

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Regards,

Phill.

---

### Post by kjohri on 2009-10-31
1. Make a text file named, say, excl containing following lines

/Music
/Music/*

2. Give the command 

tar -cvjf /media/OS/benjamin_backup.tar.bz2 -X excl benjamin

---

### Post by jesuisbenjamin on 2009-10-31
OK i figured out the correct syntax is:

```
tar -cjvf filename.tar.bz2 --exclude='/path/to/exclude' /directory/to/archive 
```

i.e. the path to exclude has to be placed before the path to archive.

---

