---
title: "Can you 'undo' a symbolic link?"
date: 2010-07-11
forum: General Help
---

### Post by Idzi on 2010-07-11
Please help.  I fear I may have effectively accidentally deleted about 700GB of data on a mounted hard drive with just one badly typed command..

I tried to create a symbolic link from my home 'Videos' directory to a directory also named 'Videos' on a mounted hard drive.  My home 'Videos' directory was completely empty and the 'Videos' directory on the mounted hard drive contained approximately 700GB of video files. 

However the creation of the symbolic link has gone disastrously wrong as I typed in the source directory and the target directory the wrong way round and used the "-f" force argument.  

Of course the result is that the 'Videos' directory on the mounted hard drive that did contain my entire video collection now links directly to my empty home 'Videos' directory!   

The exact command I typed is:

ln -sf /home/giles/Videos /media/EXTRA_STORAGE/Videos

...

Is there any way at all that I can 'UNDO' the creation of this newly symbolic link and regain access to my collection of video files?  

(If it makes any difference, I have not done anything else since creating the symbolic link... I have input in any other commands or even restarted the computer.)

Any help would be very much appreciated.  

-Idzi

---

### Post by AlphaLexman on 2010-07-11
I did that once before. 

You are F'ed.

Sorry.

---

### Post by sashoalm on 2010-07-11
Try to mount your hard drive to a different directory.

the command is something like (replace replace sdb1 with the device name of your hard drive)

sudo su
mkdir /MyHardDriveDir
mount /dev/sdb1 /MyHardDriveDir

Use the command 

fdisk -l

to find out which it is (look for the size, since you know it's 700 GB)

---

### Post by Dayofswords on 2010-07-11
i'm trying this in a folder and trying to see what i can do...

as for next time, use 'mount' as you can mount over directorys and the files that were there are not accessible, they are still there until the mount is removed, when that is done you can get to those files again, safer and does what you want i think

---

### Post by Dayofswords on 2010-07-11
i just tried it and the mock movie.avi was there

```
.:
home  media

./home:
[COLOR="RoyalBlue"]giles[/COLOR]

./home/giles:
[COLOR="RoyalBlue"]Videos[/COLOR]

./home/giles/Videos:

./media:
[COLOR="RoyalBlue"]EXTRA_STORAGE[/COLOR]

./media/EXTRA_STORAGE:
[COLOR="RoyalBlue"]Videos[/COLOR]

./media/EXTRA_STORAGE/Videos:
movie.avi  [COLOR="Cyan"]Videos[/COLOR]

```dark blue - directory
light blue - symlink

what do you get when you do```
ls -R /media/EXTRA_STORAGE/Videos
```

---

### Post by Idzi on 2010-07-11
> **sashoalm said:**
> Try to mount your hard drive to a different directory.


Thank you folks!  Some good advice and all is well :D  

sashoalm has the answer with advice to umount the drive and then re-mount it at a different mount point.  

When I browsed into the newly mounted disk there were actually two 'Videos' directories: the original 'Videos' directory with all my files in, untouched, and this contained the 'Videos' symbolic link directory I had created in error.  

...Before you ask, I did not nest the 'Videos' symbolic link that I created in the 'Videos' directory like this, as you will see from the command I typed in my original post.  So I really don't know why this is the case but I am frankly too happy to care right now!  

There's evidently a great community spirit on these forums as this is the first time I have posted and I never expected to get such a lot of help so fast! Thanks again!

---

### Post by ov3rcl0ck on 2010-07-11
Seeing as you provided the -f flag, it has deleted the directory and overwritten it with a symlink. The data is gone, however you can use complicated methods of recovery if you cannot get those videos back.

Heres a tool that may recover some of your data [http://www.r-tt.com/data_recovery_linux/](http://www.r-tt.com/data_recovery_linux/)

but I've never used it.

---

### Post by ov3rcl0ck on 2010-07-11
> **ov3rcl0ck said:**
> Seeing as you provided the -f flag, it has deleted the directory and overwritten it with a symlink. The data is gone, however you can use complicated methods of recovery if you cannot get those videos back.

Heres a tool that may recover some of your data [http://www.r-tt.com/data_recovery_linux/](http://www.r-tt.com/data_recovery_linux/)

but I've never used it.

Actually, I'm not sure if thats true, what I posted before.

Once I had python installed and I installed stackless python for development. Stackless redid the symlink of python in /usr/bin, and I had to manually uninstall stackless to fix it, I just deleted the binaries and all and the symlink went back to normal. It automatically fixed itself and pointed at my regular python install.

This may mean that the symlink is just covering the directory, and you can use the remove link function. It should return it to normal. However Hardlinks are different, and hardlinks should be used VERY sparingly.

---

### Post by Idzi on 2010-07-11
Dayofswords - looking at your last reply, it looks like my experience matches what you simulated in your test environment; after un-mounting and then re-mounting the drive, the Videos symbolic link actually ends up nested within the original Videos directory for some reason, rather than overwriting it, as it appeared at first. 

Kinda interesting I guess.  Cheers for spending the time on for me.  

-Idzi

---

