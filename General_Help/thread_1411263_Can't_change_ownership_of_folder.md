---
title: "Can't change ownership of folder?"
date: 2010-02-19
forum: General Help
---

### Post by charklii on 2010-02-19
I've tried using chown to change the owner on one of my folders - but to no luck? This is what I run on the terminal - and there's no output. And when i view the permissions of the folder it's still set to root?

charklii@Charkliiology:~$ sudo su
root@Charkliiology:/home/charklii# chown charklii "/old/charklii"
root@Charkliiology:/home/charklii#

Thanks to anyone who can help out a beginner..

---

### Post by Iowan on 2010-02-19
Stretching my memory a bit...
Try **sudo -i**

---

### Post by argos3016 on 2010-02-19
gksudo nautilus
properties
right click on your home folder
permissions
....

---

### Post by AudioDef on 2010-02-19
The quotes aren't necessary. For a directory, you might also want the recursive switch -R:

chown -R username /thisdir/thatdir/anydir

---

### Post by charklii on 2010-02-19
Thanks all for the replies.. none of the suggestions have worked - however **gksudo nautilus **did output some errors... and once the browser opened it appeared as though I'd be able change owner (it wasn't grayed out) but it immediately switched back to root whenever i selected "charklii - Charles"..

This is the output [PHP]root@Charkliiology:~# gksudo nautilus

(nautilus:1890): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:1890): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1890): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1890): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension[/PHP]

---

### Post by argos3016 on 2010-02-19
That "trick" worked for me always

---

### Post by Girya on 2010-02-19
When I tried to add a user /old/charklii to my system it complained about slashes. is there a user named /old/charklii on your system?

---

### Post by charklii on 2010-02-19
> **Girya said:**
> When I tried to add a user /old/charklii to my system it complained about slashes. is there a user named /old/charklii on your system? Nope, /old/charklii is the folder I want to change ownership of. I want to give the user charklii that ownership.

---

### Post by Girya on 2010-02-19
> **charklii said:**
> Nope, /old/charklii is the folder I want to change ownership of. I want to give the user charklii that ownership.

duh my bad

---

### Post by Girya on 2010-02-19
whats the output of:

 ```
ls -l /old/charklii
```

---

### Post by charklii on 2010-02-19
output of ls -l /old/charklii

charklii@Charkliiology:~$ ls -l /old/charklii
total 113
-rwxrwx--- 1 root plugdev   349 2009-12-17 14:46 AutoHotkey.ahk
drwxrwx--- 1 root plugdev  4096 2010-02-16 17:04 Documents
drwxrwx--- 1 root plugdev  4096 2010-02-16 17:04 Downloads
drwxrwx--- 1 root plugdev  4096 2009-12-18 18:39 methlab
drwxrwx--- 1 root plugdev 81920 2010-02-18 12:54 Music
-rwxrwx--- 1 root plugdev    29 2009-12-18 18:05 music.sh
-rwxrwx--- 1 root plugdev     0 2009-12-18 18:03 music.sh~
drwxrwx--- 1 root plugdev  4096 2010-02-16 17:06 Pictures
drwxrwx--- 1 root plugdev     0 2009-12-18 17:29 Podcasts
drwxrwx--- 1 root plugdev  8192 2010-02-18 12:54 TEMP
drwxrwx--- 1 root plugdev     0 2009-11-04 15:35 todo
drwxrwx--- 1 root plugdev  4096 2010-02-18 23:49 Videos
drwxrwx--- 1 root plugdev  4096 2009-12-20 16:09 www
charklii@Charkliiology:~$

---

### Post by charklii on 2010-02-20
The problem here was that the folder I wanted to change ownership of was where a NTFS partition was mounted - and I discovered eventually that NTFS doesnt have the same file permissions as ext3... so I don't know if there's a way to work around this and keep the NTFS format.. but as for me, I just formated the partition in ext3 after doing apropriate backups, etc...

---

### Post by bjk03 on 2010-02-20
> **AudioDef said:**
> The quotes aren't necessary. For a directory, you might also want the recursive switch -R:

chown -R username /thisdir/thatdir/anydir

Would ```
sudo chown -R username /thisdir/thatdir/anydir
``` work? I think that's way it should be. Ubuuntu doesn't like the su command.

---

### Post by tad1073 on 2010-02-20
> **charklii said:**
> The problem here was that the folder I wanted to change ownership of was where a NTFS partition was mounted - and I discovered eventually that NTFS doesnt have the same file permissions as ext3... so I don't know if there's a way to work around this and keep the NTFS format.. but as for me, I just formated the partition in ext3 after doing apropriate backups, etc...

edit your fstab to auto mount the ntfs partiton and give it theses permissions:

```
UUID=the_uuid_of_your_ntfs_partition    /where_it_is/to_be_mounted    ntfs    defaults,nls=utf8,uid=1000,gid=1000,fmask=137,dmask=027    0    0

```to find the uuid

```
sudo blkid
```

---

### Post by AudioDef on 2010-02-22
> **bjk03 said:**
> Would ```
sudo chown -R username /thisdir/thatdir/anydir
``` work? I think that's way it should be. Ubuuntu doesn't like the su command.

Yep!

Also, do not mount another file system to a directory where you already have files. Create a new, empty directory for this purpose.

---

