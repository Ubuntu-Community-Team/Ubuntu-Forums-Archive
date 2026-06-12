---
title: "can rsync sync more than one folder or directory at the same time?"
date: 2010-11-05
forum: General Help
---

### Post by gandaran on 2010-11-05
or how do I select just three folders to sync from a directory?
thanks

---

### Post by Quarkrad on 2010-11-05
I'm a newbie so not really qualified to reply. But yes - I use rsync and backup my ubuntu Home folder and another folder on a separate NTFS partition to a 2nd disk in my system.  I use Gadminrsyn which gives me an easy GUI.  Search for rsync in the Software Download and you will see Gadminrsync.  You create a backup and then list the folders you want backed up.

---

### Post by gandaran on 2010-11-05
> **Quarkrad said:**
> I'm a newbie so not really qualified to reply. But yes - I use rsync and backup my ubuntu Home folder and another folder on a separate NTFS partition to a 2nd disk in my system.  I use Gadminrsyn which gives me an easy GUI.  Search for rsync in the Software Download and you will see Gadminrsync.  You create a backup and then list the folders you want backed up.
thanks
tried Gadminrsyn but I'm finding it a bit complicated for the simple task of just sync files to a flash drive, I was more looking into using Grsync, if I just could find a way to select three or four folders from a given directory I would be very happy with it.

---

### Post by dr_duck on 2010-11-05
How about:

```
#!/bin/bash

rsync -avz /source/folder1/ /backup/folder1/
rsync -avz /source/folder2/ /backup/folder2/
rsync -avz /source/folder3/ /backup/fodler3/
```save it as ~/bin/dobackup
```
chmod +x ~/bin/dobackup
```Then run it whenever you want, or set it up so that when you plug in a specific usb drive it runs automatically (hint: google "custom udev rules"), or set it as a cron job to run whenever you want  Simple & easy.

If you want, you can get rsync to write its output to a log file so you can see what's happened as well
You can also put some basic error checking in: if the required usb drive is not mounted, try to mount it, if that fails, print an error message (you can even make it use ubuntu's notifier) and exit

You can also do it the other way: rsync a whole directory (eg your home) and exclude certain directories and file (eg, don't sync .bak files, don't sync my temp folders...) from the sync

---

### Post by gandaran on 2010-11-05
> **dr_duck said:**
> How about:

```
#!/bin/bash

rsync -avz /source/folder1/ /backup/folder1/
rsync -avz /source/folder2/ /backup/folder2/
rsync -avz /source/folder3/ /backup/fodler3/
```save it as ~/bin/dobackup
```
chmod +x ~/bin/dobackup
```Then run it whenever you want, or set it up so that when you plug in a specific usb drive it runs automatically (hint: google "custom udev rules"), or set it as a cron job to run whenever you want  Simple & easy.

If you want, you can get rsync to write its output to a log file so you can see what's happened as well
You can also put some basic error checking in: if the required usb drive is not mounted, try to mount it, if that fails, print an error message (you can even make it use ubuntu's notifier) and exit

You can also do it the other way: rsync a whole directory (eg your home) and exclude certain directories and file (eg, don't sync .bak files, don't sync my temp folders...) from the sync
I know a script with multiple commands would work but what I was looking for was to load two or more source directories/folders in one single rsync command.
looks like this isn't a rsync feature so I am giving up now and closing the thread.
thank you all.

---

### Post by anglican on 2010-11-05
[QUOTE=dr_duck;10075023]How about:

```
#!/bin/bash

rsync -avz /source/folder1/ /backup/folder1/
rsync -avz /source/folder2/ /backup/folder2/
rsync -avz /source/folder3/ /backup/fodler3/
```You could achieve exactly the same result with:
```
rsync -avz /source/folder1 /source/folder2 /source/folder3 /backup/
```rsync works very like a "cp" copy.

H

---

### Post by gandaran on 2010-11-05
> **anglican said:**
> [QUOTE=dr_duck;10075023]How about:

```
#!/bin/bash

rsync -avz /source/folder1/ /backup/folder1/
rsync -avz /source/folder2/ /backup/folder2/
rsync -avz /source/folder3/ /backup/fodler3/
```You could achieve exactly the same result with:
```
rsync -avz /source/folder1 /source/folder2 /source/folder3 /backup/
```rsync works very like a "cp" copy.

H
thats what I have been trying all the time but doesn't work!

---

### Post by anglican on 2010-11-08
> **gandaran said:**
> [QUOTE=anglican;10075401]
thats what I have been trying all the time but doesn't work!In what way doesn't it work?

H

---

### Post by gandaran on 2010-12-15
> **anglican said:**
> [QUOTE=gandaran;10075552]In what way doesn't it work?

H
anglican
sorry for the late answer!
indeed the rsync command works with multiple directories but run from the command line, what I was trying to achieve was using Grsync to sync more than one directory in one setting but seems this doesn't work, I don't know why since Grsync runs the same rsync command!
so I have programed my own small backup tool (attachment) which does the job just like I want.  
thanks

---

