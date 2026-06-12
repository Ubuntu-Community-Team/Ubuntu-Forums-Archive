---
title: "Trouble with symlinks"
date: 2010-08-25
forum: General Help
---

### Post by cmfarley19 on 2010-08-25
I am running Ubuntu 9.04 Jaunty Jackalope. I have two 40gb drives.
Drive 1, /dev/sda2 has / (root) mounted on it.  Drive 2, has just a generic /data partition it.  I use drive 2 to store my music (really my media)library "/data/Music". I added a bunch of audio books last week and have become dangerously low on space (<500MB).
Drive 1 has gobs of space on it.  So I got the idea of creating a directory on drive 1, "/More Music" and move the audio books there and create symlinks to them. So where I once had 
```
/data/Music/Audiobooks/...
```
I would now have 
```
/data/Music/Audiobooks -> /More Music/Audiobooks/
```
As root, I created the symlink in the following manner:
```
ln -s /More\ Music/Audiobooks/ /data/Music/Audiobooks
```
And ls -l /data/Music/|grep -i audiobooks yields the following:
```
lrwxrwxrwx  1 root     root       23 2010-08-25 09:45 Audiobooks -> /More Music/Audiobooks/
```
As a regular user I can navigate to /data/Music/Audiobooks and view the contents and all seems well.
The problem I am having is /data is being served as a windows share via samba.  I can get to anything on /data just fine from my windows pcs, except for /data/Music/Audiobooks.  When I try to access it from iTunes (or any other program) I get "Z:\Music\Audiobooks is not accessable. Access is denied."
Is this a permissions thing or something wrong in the way I created the symlink?
```
lrwxrwxrwx  1 root     root       23 2010-08-25 09:45 /data/Music/Audiobooks -> /More Music/Audiobooks/
drwxrwxrwx   3 root root 4.0K 2010-08-25 09:43 /More Music
drwxrwxrwx 3 cmfarley cmfarley 4.0K 2010-08-14 14:42 /More Music/Audiobooks
```

Any suggestions?

---

### Post by dv3500ea on 2010-08-25
Windows doesn't support symlinks.

Try sharing the /More Music folder (Right click -> Sharing Options)

---

### Post by cmfarley19 on 2010-08-25
Uh, really...

This actually solved the problem:
[http://www.compdigitec.com/labs/2010/03/30/how-to-enable-symlink-following-in-samba/](http://www.compdigitec.com/labs/2010/03/30/how-to-enable-symlink-following-in-samba/)

---

