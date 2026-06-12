---
title: "backing up an encrypted home folder"
date: 2012-09-09
forum: General Help
---

### Post by lmm5247 on 2012-09-09
i've been dual-booting win7 and ubuntu for quite some time, but i recently wiped Win7 off my HDD and installed ubuntu 12.04, loving it so far! :D

i had a few questions about encryption and backups. i'm running 12.04 64-bit and i've encrypted my home folder at installation.

1) when i login, my login password decrypts all my files. from here, i can copy files to flash drives (for use on another computer) and they will be unencrypted, correct?

2) from what i understand, the home folder is actually empty, and /home/.ecryptfs actually holds all my encrypted files. when i login, the OS thinks that everything is in /home, but it's really not. is this correct? is the below link correct?
[HTML]http://ubuntuforums.org/showpost.php?p=12197456&postcount=12[/HTML]

3) if i wanted to backup my /home folder, what would be the best way? i was thinking about using rsync to an external HDD. if i'm logged in while i do this, are my files stored in an unencrypted format?
[HTML]https://help.ubuntu.com/community/rsync?highlight=%28\bCategoryBackupRecovery\b%29[/HTML]

4) this is probably a stupid question, but i have my dropbox folder in /home/$user/dropbox. are my files there encrypted? from what i understand, they are encrypted on my HDD (in the event my laptop is lost/stolen) but not on dropbox, because dropbox never sees them in the encrypted format, right?

thanks in advance, i appreciate any help! :)

---

### Post by jerome1232 on 2012-09-09
Personally I would just use the built in utility deja-dup (called backup in your menu's) You can select which folders to backup, where to backup (be it network share, local drive, the cloud etc..) It allows you to encrypt your backup or leave it unencrypted ( if you just rsync/tar or whatever your backups will be unencrypted) It does incremental backups, meaning it only backs up files which have changed since the last backup, which saves space and time. It allows you to restore from previous backups based on the date they were created. You can also set it to routinely backup your files at regular intervals.

it's a fairly decent, easy to use backup solution imho.


> this is probably a stupid question, but i have my dropbox folder in  /home/$user/dropbox. are my files there encrypted? from what i  understand, they are encrypted on my HDD (in the event my laptop is  lost/stolen) but not on dropbox, because dropbox never sees them in the  encrypted format, right?

This is correct.

---

### Post by d3v1150m471c on 2012-09-09
pipes are your friend :-)
```

# compress/encrypt
tar -hc /home/$USER/ | gpg -c -o $USER.tar.gpg

# decrypt/explode
gpg -d $USER.tar.gpg | tar xf -

```

---

### Post by newb85 on 2012-09-09
Deja Dup is extremely easy to set up.  My biggest beef with it is that it uses rsync.  Consequently, the backup files are a format that cannot be browsed or selectively extracted.

The previous post is a great example of pipes, but there are probably a few more options you want to include in your tar commands.  You should probably look over the manual entry for tar.

```
$ man tar
```

---

### Post by jerome1232 on 2012-09-09
> **newb85 said:**
> Deja Dup is extremely easy to set up.  My biggest beef with it is that it uses rsync.  Consequently, the backup files are a format that cannot be browsed or selectively extracted.


Actually, if you pop open nautilus, browse to some folder you have backuped up, hit alt, search for "resto", press enter, a gui will allow you to selectively restore files to that folder.

I understand you can use duplicity from the command line to manually manipulate the backups.

---

### Post by lmm5247 on 2012-09-09
> **jerome1232 said:**
> Actually, if you pop open nautilus, browse to some folder you have backuped up, hit alt, search for "resto", press enter, a gui will allow you to selectively restore files to that folder.

I understand you can use duplicity from the command line to manually manipulate the backups.

but if the files were on an external drive. i could not just browse to that drive and view a single file. correct? i'd have to restore it first?

---

### Post by jerome1232 on 2012-09-09
> **lmm5247 said:**
> but if the files were on an external drive. i could not just browse to that drive and view a single file. correct? i'd have to restore it first?

That is correct. If you want to be able to do that you'd be better of with rsync, or tar, and using cron to schedule the backups.

edit: I should note, duplicity from the command line CAN list out files contained in the backup.

---

### Post by d3v1150m471c on 2012-09-10
edit:
..i assume you're wanting to pull the backup to another machine on the network

server
```

tcpserver 192.168.1.2 8080 cat backup.tar.gpg

```

client
```

tcpcat 192.168.1.2 8080 > backup.tar.gpg

```

---

