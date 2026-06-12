---
title: "rsync overwrites the same files every time"
date: 2012-03-08
forum: General Help
---

### Post by Kissell on 2012-03-08
I have cron regularly run a script to copy new videos from a file server to my laptop.  This keeps my laptop up-to-date so I can watch a new movie on the road.  But I ran it manually today and noticed it overwrites some of the same files every time I run it.  

I originally had "-grouptv" instead of "-rtv" but have also tried "-av" and "-auv"...  and I added the "--modify-window 1" and changed it to "--modify-window 60" but still the problem occurs... 

Most files don't transfer, because they already exist, but some files that have been unmodified in any way get copied over again.  

This is over a samba share mounted using smbfs, the source file system is XFS and the destination is BtRFS.

```

PATH_SERVER_MOVIES_NEW="/media/Data/XBMC/New Movies"
PATH_LOCAL_MOVIES_NEW="/home/myuser/Data-Laptop/XBMC/New Movies"
mkdir "$PATH_LOCAL_MOVIES_NEW" -p

  # COPY NEW MOVIES CONTENT FROM XBMC SERVER TO LOCAL LAPTOP
  echo " "
  echo "Copying any missing (new) files from $PATH_SERVER_MOVIES_NEW..."
  sudo rsync -rtv --progress --modify-window 60 --delete "$PATH_SERVER_MOVIES_NEW"/* "$PATH_LOCAL_MOVIES_NEW"
  echo " "

```

---

### Post by Kissell on 2012-03-08
Not an rsync problem...  

My bad...  a clean up script was removing anything older than X days...  to keep the laptop hard drive space free...  the server files being copied every time were ones that had been deleted by the clean up script.  They were one day off...  

Changed the laptop to only delete things X-1 days old, so that it'll already be deleted on the server before rsync runs...

---

