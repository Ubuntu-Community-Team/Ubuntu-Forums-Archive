---
title: "Persistant rsync"
date: 2010-05-30
forum: General Help
---

### Post by ipburbank on 2010-05-30
Hey, so I have a slow 3TB usb drive that I keep my video projects on, but when I'm working on a project I want to have the files on my main HD so that the video editing is less painful. So here is my question: is there a way to have a folder on my main computer that syncs files *as they are needed* to my main drive, then when they are edited sync them to the USB drive again?

So if I have a folder with 100 clips on my USB drive, can I sync just the directory listings to the local folder, then when I add a video to my project file and it is read by the video editing software, then just that file is synced to my local folder? Then, when I close the terminal with this app running, or some other signal the local folder is destroyed (all of the files are synced to the USB drive once they are changed)

If this doesn't exist, how hard would it be to do?

Istvan.

---

### Post by Snow986 on 2010-05-30
Sounds like you could create two scripts that are interactive (or not) and just run them when needed.

```

#!/bin/bash
echo "Enter the directory to sync to local drive"
read inDIR
echo "Enter the directory of where to put the dir"
read newDIR
rsync -auv $inDIR $newDIR

```

then for the resync

```

#!/bin/bash
echo "Enter the directory to sync to usb drive"
read inDIR
echo "Enter the directory of where to put the dir"
read usbDIR
rsync -auv $inDIR $usbDIR
rm -rf $inDIR

```

then just chmod the scripts and run when necessary.

You could even go all out and create a right click gui menu entry to run similar scripts that would rsync the right clicked directory to a predetermined place.

---

### Post by sdennie on 2010-05-30
The above suggestion is the right idea I think.  I would do it slightly differently though.  I'd add the following to ~/.bashrc

```

getdir() { rsync -av "/path/to/usb/$1" .; }
putdir() { rsync -av . "/path/to/usb/$1"; }
checkdir() { rsync -avn . "/path/to/usb/$1"; }

```

(Then type "source ~/.bashrc")

If you change /path/to/usb to be the location of your USB drive, this essentially gives you a very primitive version control system.  From the commandline, you might do something like:

```

cd ~/Projects
getdir project1            # Bring over a directory
cd project1
... Edit some files ...
checkdir project1
... check if the changes look right ...
putdir project1            # Put it back on USB

```

Edit:
I forgot the requirement to delete.  In which case, change putdir to be:

```

putdir() { rsync -av . "/home/sdennie/tmp/$1" && rm -rf `pwd` && cd ..; }

```

That will erase the directory you are in but only if the rsync is successful.

Edit 2:
Changed the usage to add a "cd project1" as that is the real usage case.

Edit 3: Add a "cd .." to putdir to drop back a directory level.  Final edit.  I promise.

---

### Post by ipburbank on 2010-05-31
Thanks! Those look like great first-scripts, but as far as I can tell one of the most important features is missing - Only sync the files that are requested. The reason for doing this instead of copying the folder over to my hard drive, then copy->mergeing it back when I'm done is there are folders with hundreds of multi-gig files (1080p videos) of which only 10-20 are used. Instead of copying them over at the start, I was thinking something more like this:

Links are made for each file, so there is no data on the HD, then when my editing software tries to read the link *then* the script copies just that file over and replaces the link. It's a minimalist approach to the transfer. There will be a few seconds lag during the copy in my editing software, but after the initial transfer the file is local for the rest of the session.

From what I can tell that is missing from the scripts, but I may be wrong. Thanks for the replies, Istvan.

---

### Post by sdennie on 2010-05-31
> **ipburbank said:**
> 
Links are made for each file, so there is no data on the HD, then when my editing software tries to read the link *then* the script copies just that file over and replaces the link. It's a minimalist approach to the transfer. There will be a few seconds lag during the copy in my editing software, but after the initial transfer the file is local for the rest of the session.


I don't think you'll be able to achieve that level of automation without finding/writing a FUSE level filesystem.  What you are describing is similar to UnionFS or NFS with FS-cache but, not quite.  It's possible that there is already a filesystem type that handles exactly what you are asking for though so, I would do some research on all the available user-space filesystems on linux (there are a number of them).

---

