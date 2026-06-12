---
title: "Random, very odd behaviour crashing rsync"
date: 2010-04-13
forum: General Help
---

### Post by switch10 on 2010-04-13
I am running rsync like this:
```
 rsync -auv --progress --stats --delete /home/dave/Music/ /media/server/Music 
```

rsync stops with this in my terminal...

```
 cannot send long-named file "/media/server/Music/G/Grateful Dead - dicks picks vols 23 - 29/dicks picks vols 23 - 29/vol 23 - 1972 - 3 cd/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/resume.ogg/Z/" 
```

This is looped over and over again, filling my terminal.

This has been happening since I can remember, and It's a different file every time.  I can fix it by SSHing into my NAS, and removing the problematic directory, in this case, /media/server/Music/G/Grateful Dead, and then if I run rsync again, everything works fine.  The weird thing is the file resume.ogg does not exist in that directory on the source machine, it is in another directory all together.  This also seems to happen completely at random.  

Does anyone know whats going on here?

Thanks, 

Dave

---

### Post by switch10 on 2010-04-14
Bump.  Any ideas??  Anyone??

---

### Post by switch10 on 2010-04-16
I am still having trouble with this...  I found that if I change the target dir to, say, a USB HDD, it does not give me the error, and rsync completes as it should.  It has something to do with transferring over the network...

Also, the target dir I am trying to transfer to is a symbolic link on my local system.  Could that cause a problem?

Any ideas at all would be greatly appreciated.

Thanks, 

Dave

---

### Post by switch10 on 2010-04-16
hmm..  I may have fixed this issue.  Instead of using the link, I used root@IPadress:/dir, it seems to be working much better, and it has deleted a few bad file names that never existed... 

I will let it run and mark thread as solved if it does work...

---

### Post by jaccall on 2010-04-16
Hi,

I am having the same issue but am using rsnapahot to backup our campus data by mounting Novell Volumes (GROAN), Windows Shares and our N7700Pro Thecus NAS on a single Ubuntu 9.10 server to do all the backup tasks.

I think the problem is more than you suggest. I was doing the same by excluding directories causing the problem but I have been working on this for a month and am getting nowhere :(

Here is my fstab entries and they are ok as far as I can tell:

```
/10.16.49.105/backups  /media/backups_primary cifs iocharset=utf8,credentials=/home/super/.smbcredentials,uid=1000,gid=1000,noperm 0 0
//10.16.49.104/backups  /media/backups_secondary cifs iocharset=utf8,credentials=/home/super/.smbcredentials,uid=1000,gid=1000,noperm 0 0
//10.16.48.33/dvdweekly /media/mesha   cifs iocharset=utf8,credentials=/home/super/.mesha-pass,uid=1000,gid=1000,noperm 0 0 
10.16.48.32/super.lumen /media/lcc3 ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.32,passwdfile=/home/super/.lcc3-pass 0 0
10.16.48.34/super.lumen /media/zenas2 ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.34,passwdfile=/home/super/.zenas2-pass 0 0
10.16.48.47/super.lumen /media/sweb ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.47,passwdfile=/home/super/.sweb-pass 0 0
``` 


And here is what rsnapashot calls:
```
/usr/bin/rsync -apl --delete --numeric-ids --relative --delete-excluded \
    --iconv=cp850,utf8 --exclude=autorun.inf --exclude=.DS_Store \
    --exclude=*.EAR --exclude=*.tmp --exclude=*.iso --exclude=*.exe \
    --exclude=*.lnk --exclude=*.ini --exclude=*.db --exclude=*AART* \
    --exclude=*GABBEDYA* --exclude=*STILLITL* \
    --link-dest=/media/backups_primary/hourly.1/staff/ \
    /media/sweb/STAFF/USERS /media/backups_primary/hourly.0/staff/ 
```

I finally got one complete backup in the hourly.1 snapshot...but now the same set of files has caused this problem again today. Nothing has changed much as it's college break at the moment so no-one around :(

I am at a loss...please help someone.

Cheers,
--
Lou S

---

### Post by cjhabs on 2010-04-16
With the repeating file in the message, my guess is that there is a symbolic link that is pointing back to itself via another link.

---

### Post by switch10 on 2010-04-16
> **jaccall said:**
> Hi,

I am having the same issue but am using rsnapahot to backup our campus data by mounting Novell Volumes (GROAN), Windows Shares and our N7700Pro Thecus NAS on a single Ubuntu 9.10 server to do all the backup tasks.

I think the problem is more than you suggest. I was doing the same by excluding directories causing the problem but I have been working on this for a month and am getting nowhere :(

Here is my fstab entries and they are ok as far as I can tell:

```
/10.16.49.105/backups  /media/backups_primary cifs iocharset=utf8,credentials=/home/super/.smbcredentials,uid=1000,gid=1000,noperm 0 0
//10.16.49.104/backups  /media/backups_secondary cifs iocharset=utf8,credentials=/home/super/.smbcredentials,uid=1000,gid=1000,noperm 0 0
//10.16.48.33/dvdweekly /media/mesha   cifs iocharset=utf8,credentials=/home/super/.mesha-pass,uid=1000,gid=1000,noperm 0 0 
10.16.48.32/super.lumen /media/lcc3 ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.32,passwdfile=/home/super/.lcc3-pass 0 0
10.16.48.34/super.lumen /media/zenas2 ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.34,passwdfile=/home/super/.zenas2-pass 0 0
10.16.48.47/super.lumen /media/sweb ncp uid=super,gid=super,mode=755,owner=super,A=10.16.48.47,passwdfile=/home/super/.sweb-pass 0 0
``` 


And here is what rsnapashot calls:
```
/usr/bin/rsync -apl --delete --numeric-ids --relative --delete-excluded \
    --iconv=cp850,utf8 --exclude=autorun.inf --exclude=.DS_Store \
    --exclude=*.EAR --exclude=*.tmp --exclude=*.iso --exclude=*.exe \
    --exclude=*.lnk --exclude=*.ini --exclude=*.db --exclude=*AART* \
    --exclude=*GABBEDYA* --exclude=*STILLITL* \
    --link-dest=/media/backups_primary/hourly.1/staff/ \
    /media/sweb/STAFF/USERS /media/backups_primary/hourly.0/staff/ 
```

I finally got one complete backup in the hourly.1 snapshot...but now the same set of files has caused this problem again today. Nothing has changed much as it's college break at the moment so no-one around :(

I am at a loss...please help someone.

Cheers,
--
Lou S

yes, make sure you --exclude anything that would cause a loop.  i.e. backing up /media, or any symbolic links to it.  

The issue is solved for me, I have run rsync a few different times, with different options, and it has not failed once.

so instead of running it through a symbolic link like in my first post, I am running it like this:
```
rsync -auv --no-t --progress --stats --delete /home/dave/Music/ root@192.168.1.106:/mnt/HD_a2/Music
```

So in your case (I am using your first entry in /etc/fstab), as your taget dir you would use ```
root@10.16.49.105:/backups/....
```

instead of:

```
/media/backups_primary/hourly.0/staff/
``` 

I hope that works for you.  It seems to be working great for me.

---

