---
title: "Cannot delete PhotoRec Backup"
date: 2009-12-06
forum: General Help
---

### Post by deadpool47 on 2009-12-06
I had an issue some days ago with my external HDD which caused me to lose my video files on the drive. I used PhotoRec to back them up, but now that it's done backing all of my movies, I can't remove the backed up files off my main drive. My 750GB hard drive is full to the brim with data and I can't remove it. When I go to change the permissions on it, the prompts tell me "You are not the Owner, so you Can not change these permissions" which is BS because I am the owner!

Okay, to break it down, I wanna delete this crap, but my own computer won't let me. Is there a simple solution to this?

---

### Post by llamabr on 2009-12-06
I guess 'owner' doesn't mean the person who own's the disk, it means the user who has permission to edit the files.  you can review the file permissions by doing:

```
ls -l
```

Anyway, try deleting it with sudo, rather than without.

---

### Post by deadpool47 on 2009-12-06
I just moved from Windows to Ubuntu, so I'm retarded in this department. Can you show me with a command code how to do so?

---

### Post by bumanie on 2009-12-06
You should be able to delete the files as root. Go to terminal (Applications --> Accessories --> Terminal) and type > gksudo nautilusFollwed by enter, put in your password (which does not display any visual output) and hit enter. This gives you root privileges in graphical mode. You should be able to navigate to the files you wish to remove, via filesystem then to /home or /media, depending where the files you need to remove are  - but remember, you will be in super user mode and anything you remove will be gone forever, so be careful. 
Hope this helps.

---

### Post by deadpool47 on 2009-12-06
> **bumanie said:**
> You should be able to delete the files as root. Go to terminal (Applications --> Accessories --> Terminal) and type Follwed by enter, put in your password (which does not display any visual output) and hit enter. This gives you root privileges in graphical mode. You should be able to navigate to the files you wish to remove, via filesystem then to /home or /media, depending where the files you need to remove are  - but remember, you will be in super user mode and anything you remove will be gone forever, so be careful. 
Hope this helps.

It's telling me I don't have enough disk space it run it. Now what?

---

### Post by bumanie on 2009-12-06
Post the output of > df -hSounds as though your filesystem is completely full - computers don't behave normally when this is the case.

---

### Post by deadpool47 on 2009-12-06
does that mean if I turn off this PC, I won't be able to boot it again, doesn't it? Am I in trouble?

---

### Post by bumanie on 2009-12-06
Just post the output of the command and we will see if we can fix things. There are a couple of ways that can help free up some space - just want to see how full the filesystem is first.

---

### Post by deadpool47 on 2009-12-06
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             679G  668G     0 100% /
udev                  1.6G  256K  1.6G   1% /dev
none                  1.6G  508K  1.6G   1% /dev/shm
none                  1.6G   84K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sdb1             932G  555G  377G  60% /media/1DF7-382A


I'm no computer genius, but I can see it says Use%=100. I have no other data on this drive, this is a clean install and all I have on here is that PhotoRec crap.

---

### Post by bumanie on 2009-12-06
OK - go to terminal and put in > sudo apt-get autoremoveAfter the operation has completed, post the output of>  df -h again

---

### Post by aysiu on 2009-12-06
```
sudo apt-get clean
``` should help clear up *some* space.

To delete the Photorec backups, use ```
gksudo nautilus
``` so you have permission. Make sure to use Shift-Delete instead of Delete. Shift-Delete will delete the backups immediately. Delete will just move them to the root trash, which will still take up room on the drive.

---

### Post by deadpool47 on 2009-12-07
no change

---

### Post by aysiu on 2009-12-07
> **deadpool47 said:**
> no change
Are you able to delete the Photorec backup files or not?

If, for some reason, you can't do anything because the hard drive is absolutely full, boot up a live CD (or live USB using UNetBootIn) and then use that to mount your drive (Places > and then select the drive) and delete the files.

---

### Post by deadpool47 on 2009-12-07
I don't have my disk with at the moment. I'm staying at a relatives house because I had surgery on my arm early last week. I'd have to go home to do so, but I'll do that maybe tomorrow or the next day.

Thanks for the help.

---

