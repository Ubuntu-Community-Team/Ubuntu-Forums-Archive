---
title: "Really, Really need help restoring a backup."
date: 2009-12-26
forum: General Help
---

### Post by bootdoc on 2009-12-26
I installed UUE2.5 karmic the other day only to get out of disk space errors.  So I used sbackup to backup the home folder which includes two accounts.  After reinstalling uue2.5 I tried restoring the backup file.  NOTHING.  I get a file called tmpW34y that is locked in the destination folder /home rather than a restored /home.  I really could use some help figuring this out.  I used sbackup once before on a clients laptop and it worked flawlessly.  Now I can not get a single folder out of it on my machine.:(

---

### Post by bodhi.zazen on 2009-12-27
Hard to tell from what you posted.

Here is a how-to :

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

I would look at the back up files, are they corrupt ? How big are they ?

---

### Post by bootdoc on 2009-12-27
I don't think they are corrupt.  it is about 4gigs.  I read the tutorial and tried running sretore in terminal.  Still all I get is a file named /home/tmpZLz0UC.  It is owned by root. when I change the permissions and open the folder there is nothing in it.

Like I said previously, I ran sbackup on a clients machine and restored the whole file structure.  everything was back. I don't get it?!:confused:

I am getting really frustrated.

---

### Post by bootdoc on 2009-12-27
after running sudo srestore.py /media/disk/2009-12-23_12.06.30.198497.charlie-desktop.ful /home

Traceback (most recent call last):
  File "/usr/sbin/srestore.py", line 157, in <module>
    ret = r.restore( sys.argv[1], sys.argv[2] )
  File "/usr/sbin/srestore.py", line 100, in restore
    shutil.move( src, dst )
  File "/usr/lib/python2.6/shutil.py", line 264, in move
    copy2(src, real_dst)
  File "/usr/lib/python2.6/shutil.py", line 99, in copy2
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 52, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: '/home/tmpZLz0UC/home/charlie/.amarok-nightly/tmp/ksocket-charlie/klauncherMT2927.slave-socket

---

### Post by bodhi.zazen on 2009-12-27
Try :

```
sudo srestore.py /media/disk/2009-12-23_12.06.30.198497.charlie-desktop.ful /home/charlie
```

Or can you run from a gui ? perhaps you will get some useful information.

---

### Post by bootdoc on 2009-12-29
the above command restored some hidden folders from the archive but did not restore all my data folders.  I am trying the same command using /home/prisca to try to get my wifes data back.

sudo srestore.py /media/disk/2009-12-23_12.06.30.198497.charlie-desktop.ful /home/prisca /home/prisca/old
Traceback (most recent call last):
  File "/usr/sbin/srestore.py", line 159, in <module>
    ret = r.restore( sys.argv[1], sys.argv[2], sys.argv[3] )
  File "/usr/sbin/srestore.py", line 112, in restore
    shutil.move( os.path.join(tdir,spath), dpath )
  File "/usr/lib/python2.6/shutil.py", line 264, in move
    copy2(src, real_dst)
  File "/usr/lib/python2.6/shutil.py", line 99, in copy2
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 52, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: '/home/prisca/tmpJ0OF37/home/prisca'

so the above command should have restored /home/prisca to /home/prisca/old but instead it creates a folder called tmpJ00F37 that is empty.  It looks as if srestore is looking for a folder call /home/prisca/tmpJ00F37 /home/prisca.

---

### Post by bootdoc on 2009-12-29
well, I finally figured out that you can open the backup folder and explore the tarball.  As it turns out sbackup only made a backup of the hidden folders in my home folder.  All of my other data and all of my wifes home folder had not been backed up even though the folder hierarchy is listed in the backup.  This is pretty tragic for me.  I now have to tell my wife that 3 yrs of stuff is gone.  It is very frustrating that software that is unreliable is in the repos.  

As I said earlier,  simple backup/restore worked flawlessly once.  

I never got an error message saying that sbackup exited before it was done. No progress bar.  I believed the backup was good because all the folders and files were available in the restore dialog.:mad:

I'll never use sbackup again unless several improvements are made.
1 error reporting
2 progress report
3 one dialog for config and restore
4 easier backup recognition

---

### Post by bodhi.zazen on 2009-12-29
I am sorry for your loss. Have you looked at any type of data recovery strategy ? Test disk or photorec ?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If possible, STOP running your system from the HD and boot a Live CD.

I think the lesson to learn, it is not a back up if you have not confirmed you can restore from it =)

---

