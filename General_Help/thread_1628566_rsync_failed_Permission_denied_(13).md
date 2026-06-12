---
title: "rsync failed: Permission denied (13)"
date: 2010-11-22
forum: General Help
---

### Post by ryharv on 2010-11-22
Hello all:

I have a Ubuntu box and just got a new hard drive.  Rather than copy everything over from my old working Ubuntu install, I wanted to install Ubuntu from scratch and then rebuild the file contents.

I have a large collection of music that I use on my mac (another computer) and like to keep sync'ed to the Ubuntu box.  The following script used to work flawlessly:


```
rsync -avz --delete --exclude-from './music_exclude_list' '/Users/ryan/Music/iTunes/iTunes Music/' 'ryan@192.168.1.200:/home/share/music'
```

I run this from the mac and it syncs all my music files to the Ubuntu box at 192.168.1.200.

With the new hard drive, I created a folder at /home/share/music and changed its user:group to ryan:ryan.  I also made sure that its permission is set to 755.  Keep in mind that /home/share/music is currently empty.

Whenever I run the script, it skips the creation of every music folder like so:


```
rsync: recv_generator: mkdir "/home/share/music/wiseguys" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
```

It repeats this message for every folder. 

At the end, rsync gives me this message:

```
sent 1612285 bytes  received 13858 bytes  130091.44 bytes/sec
total size is 218579540279  speedup is 134415.94
rsync error: some files could not be transferred (code 23) at /SourceCache/rsync/rsync-40/rsync/main.c(992) [sender=2.6.9]
```

Any ideas?

Thank you,

  Ryan

---

### Post by ryharv on 2010-11-29
Fixed my own issue...

It was that I didn't own the destination folder, root did.  So I used the chown command on the destination folder to make myself own it, not root, and problem solved.

---

### Post by mimor on 2012-06-05
A bit late: but this is probably because you need root at the other side of the ssh pipe.
Try this:
```
rsync -a -e "ssh" --rsync-path="sudo rsync" /source/path /destination/path 
```

---

### Post by sffvba[e0rt on 2012-06-05
> **ryharv said:**
> Fixed my own issue...

It was that I didn't own the destination folder, root did.  So I used the chown command on the destination folder to make myself own it, not root, and problem solved.

Seems a solution was already forthcoming.

*Thread **closed**.*


404

---

