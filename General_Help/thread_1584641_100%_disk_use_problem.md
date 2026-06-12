---
title: "100% disk use problem"
date: 2010-09-29
forum: General Help
---

### Post by NobleSavage on 2010-09-29
I have an older box still running 8.04. I'm in the process of building a new one for 10.04 and I have 10.04 on my laptop.

Now my problem is that the old box with 8.04 has basically locked up saying I've used 100% of the disk space:

> noble@nassau:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G  137G     0 100% /
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   56K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
lrm                  1014M   40M  975M   4% /lib/modules/2.6.24-28-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
gvfs-fuse-daemon      143G  137G     0 100% /home/noble/.gvfs


Other than the OS and some text files I'm not sure what is eating up all the space. Is there a command line query that I could run on the HD to look for big files or things to delete?

One think I know that is taking up a lot of space is my old pop mail. I have 2 pop mail clients and I never deleted any of the messages and there were THOUSANDS.  Is there a way to delete the old pop mail or see how much space that is taking up? 

Or in general what kind of searches could I do to look for anything that is hogging the disk space.

Thanks in advance!

---

### Post by NobleSavage on 2010-09-29
BTY I'm using Tunderbird not evolution for my mail client.

---

### Post by DaithiF on 2010-09-29
Hi, there are lots of ways of doing this, including a GUI tool [https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

or from the command line one way would be:
```
find / -size +20M -exec du -m {} \; | sort -n
```

which would give you a list in ascending order of size of all files greater than 20MB -- hopefully highlighting the hogs.

---

### Post by NobleSavage on 2010-09-29
> **DaithiF said:**
> Hi, there are lots of ways of doing this, including a GUI tool [https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

or from the command line one way would be:
```
find / -size +20M -exec du -m {} \; | sort -n
```

which would give you a list in ascending order of size of all files greater than 20MB -- hopefully highlighting the hogs.

Thanks for this. Tried the command line option and I noticed this:

198	/media/backup/2010-09-13_07.57.24.529606.nassau.inc/files.tgz
229	/media/backup/2010-09-04_07.56.44.670184.nassau.inc/files.tgz
237	/media/backup/2010-09-10_07.38.25.053920.nassau.inc/files.tgz
239	/media/backup/2010-08-26_07.41.57.679205.nassau.inc/files.tgz
247	/media/backup/2010-09-05_07.47.32.264771.nassau.inc/files.tgz
273	/media/backup/2010-09-07_07.40.44.077053.nassau.inc/files.tgz
274	/media/backup/2010-09-06_07.48.17.153105.nassau.inc/files.tgz
275	/media/backup/2010-09-08_07.47.57.642778.nassau.inc/files.tgz
281	/media/backup/2010-09-11_07.59.17.926145.nassau.inc/files.tgz
301	/media/backup/2010-09-12_07.50.41.872784.nassau.inc/files.tgz
310	/media/backup/2010-09-03_07.57.18.023213.nassau.inc/files.tgz


Now I have an external usb drive (about 700gigs) named backup.  I use Simple Backup to do daily backups. Is 8.04 reading the space on "backup" and counting it towards my total disk space?  Coincidently, I just started this backup scheme when the drive locked up and said it was 100% full.

---

### Post by NobleSavage on 2010-09-29
I just noticed that the external drive I had named "backup" was unplugged. I'm thinking simple backup couldn't find the drive so just made a new folder /media/backup and filled up my drive. 

Is that the most likely problem?

---

### Post by DaithiF on 2010-09-29
yep, sounds plausible to me!

---

