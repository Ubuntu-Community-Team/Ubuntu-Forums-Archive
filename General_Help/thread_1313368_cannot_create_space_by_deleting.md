---
title: "cannot create space by deleting"
date: 2009-11-03
forum: General Help
---

### Post by Foeburner on 2009-11-03
Hello, 

I setup an FTP folder in /var/ and its already full. I deleted about 50GBs of items but its still at 100% use and the trash can is empty. I used the program bleachbit to delete unnecessary items and still. 

I was following up this thread but it didnt help my situation. 
[http://ubuntuforums.org/showthread.php?t=1060821&page=3](http://ubuntuforums.org/showthread.php?t=1060821&page=3)

This is what I get with df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.2G  3.6G  5.2G  41% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  4.2M  497M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  164K  501M   1% /dev
tmpfs                 501M  168K  501M   1% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-13-server/volatile
/dev/md2              284G  270G  8.5M 100% /var
df: `/home/afuentes/.gvfs': No such file or directory
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-14-server/volatile
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-15-server/volatile
/dev/sr0              698M  698M     0 100% /media/cdrom0
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-16-server/volatile

```

Is there a ./trashcan in the /var/ partition?

Thanks greatly for the help. :D

---

### Post by dcstar on 2009-11-03
> **Foeburner said:**
> Hello, 

I setup an FTP folder in /var/ and its already full. I deleted about 50GBs of items but its still at 100% use and the trash can is empty. I used the program bleachbit to delete unnecessary items and still. 

I was following up this thread but it didnt help my situation. 
[http://ubuntuforums.org/showthread.php?t=1060821&page=3](http://ubuntuforums.org/showthread.php?t=1060821&page=3)

This is what I get with df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.2G  3.6G  5.2G  41% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  4.2M  497M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  164K  501M   1% /dev
tmpfs                 501M  168K  501M   1% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-13-server/volatile
/dev/md2              284G  270G  8.5M 100% /var
df: `/home/afuentes/.gvfs': No such file or directory
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-14-server/volatile
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-15-server/volatile
/dev/sr0              698M  698M     0 100% /media/cdrom0
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-16-server/volatile

```

Is there a ./trashcan in the /var/ partition?

Thanks greatly for the help. :D

```
sudo du /var
sudo du /home/.Trash-root
```

---

### Post by Foeburner on 2009-11-03
Thanks for the reply. I ran the command and got this total
 
282225288	/var

I ran the 2nd command and got 

du: cannot access `/home/.Trash-root': No such file or directory

---

### Post by wildweathel on 2009-11-03
I can think of four reasons why a deleted file wouldn't free up space:

1) Still in trash.  Shouldn't be an issue here, though, since /var shouldn't have trash.
2) Remaining [hardlinks]("http://en.wikipedia.org/wiki/Hard_link").  This ones tricky.  Basically, its possible for one file to have multiple names.  The data will only be deleted when the last name is deleted.
3) A program still has the data open.  Bittorrent clients especially can be at fault here.
4) Inconsistent file system.

So, try this:
Alt-F2:
```
gksu touch /forcefsck
```enter password
reboot

That will check your filesystems and take care of #3 and 4.  For #1 and 2, run Applications -> Accessories -> Disk Usage Analyzer.

Hope that helps.  I've never seen this problem on my own computer, though, so I'm not sure.  Good luck.

---

### Post by Foeburner on 2009-11-03
it still the same. I was originally deleting things based on the disk usage analyzer and it shows total capacity 293.6GB (273.5GB available 20.1GB) but the total of root is 157.9GB

See image here[IMG]http://s43.photobucket.com/albums/e386/bloodslayne/?action=view&current=ubuntuDiskSpace.png[/IMG].

[http://s43.photobucket.com/albums/e386/bloodslayne/?action=view&current=ubuntuDiskSpace.png](http://s43.photobucket.com/albums/e386/bloodslayne/?action=view&current=ubuntuDiskSpace.png)

---

### Post by wildweathel on 2009-11-03
Unfortunately, that line isn't very useful.  It shows total capacity, for all of your filesystems added together.  It's just plain stupid, really, but for now, ignore it.

The good news is we now have a count for /var: 154.5 GB, down from 270GB.  I'm pretty sure that running "du -sh /var" will show the same amount, but you can try it if you like.  That leaves the big question: what does "df -h /var" say?  It might have fixed itself.  Can you confirm that:

sudo du -sh /var
df -h /var 

give different values?  That's not uncommon, but a reboot and fsck should bring them back in sync. Sorry, I should have asked this in the last post.  I'm still learning, too.

---

### Post by Foeburner on 2009-11-04
The values are the same:

```

afuentes@Apollo:~$ df -h /var
Filesystem            Size  Used Avail Use% Mounted on
/dev/md2              284G  270G  796K 100% /var
afuentes@Apollo:~$ sudo df -h /var
[sudo] password for afuentes: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/md2              284G  270G  796K 100% /var

```

Whats wierd is that the count is 154.5GB but the above says differently.

---

### Post by Foeburner on 2009-11-04
i just deleted 30GBs and its still at 100% usage. I checked disk usage analyzer and it says that its only 129GB total. 

My coworkers are nagging me because they need to save to the shared folder but their files are small.

---

### Post by undecim on 2009-11-04
How are you deleting these files? If you are using nautilus, you will need to delete the .Trash folders from the root of the filesystem. (Press Ctrl+H in nautilus to view hidden files)

---

### Post by drs305 on 2009-11-04
There are user trash bins and root trash bins, and both have to be emptied. If emptying them from a browser, you have to use SHIFT-DEL or they won't be permanently removed.

User trash is at ~/.local/share/Trash
Root trash is at /root/.local/share/Trash

Here is a link on Trash and how to find and remove it:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

Freeing disk space
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Foeburner on 2009-11-04
Thank you! I've found that /var has a trash bin containing all the files I previously "deleted". I shift-deleted the items and they're deleting as we speak. I've also emptied out the user and root trashbins. 

Thank you all!!!!   =*D

---

### Post by wildweathel on 2009-11-04
Looks like I was wrong. Disk Usage Analyzer(baobab) misses trash files.  I'm gonna try that on my computer now.  Thanks for teaching me something.

Since your problem is solved, can you click on "thread tools" and mark this [solved]?

---

