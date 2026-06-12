---
title: "Huge rsync problem!"
date: 2011-07-12
forum: General Help
---

### Post by el_ricardo on 2011-07-12
I really hope someone can help me!

I've recently set up a number of PCs to sync photos stored on them to a central server, where they are then sent on to a webserver for online sales. I've used rsync to achieve the first part, and lftp for the second.

On the 1st PC (ubuntu 11.04), rsync runs every 15 minutes on a cron job with these options:

```

rsync -e ssh -varuzP /home/cyg_server/upload/ MYSERVER:/home/cyg_server/photostore/CLI/ --remove-source-files --temp-dir=/home/cyg_server/photostore/temp >> /home/cyg_server/Desktop/PhotoUploadLog.txt


```

for some reason though it doesn't send every file. It seems to skip a few every 10 or so photos (photos get added to it's upload directory every 1-5 minutes, so quite frequently). Is there anything in that command that stands out to anyone that might explain this?

The second (server) PC runs windows server 2008 with rsyncd running on cygwin (hence the username "cyg_server".

This is a serious problem as we're getting huge backlogs of files which I have to re-send manually, and we're getting constant emails from people asking where the hell their photo is!

---

### Post by SeijiSensei on 2011-07-12
If you're running rsync every fifteen minutes, only the photos that are on the machine at that time will be transferred.  New ones should be transferred the next time rsync is executed.  rsync builds its list of files to transfer when it starts; it doesn't reexamine the directory dynamically during the transfer.

Either you'll have to increase the frequency of syncs, or use a different method.  Why not export the directory off the central server with NFS and write the photos there directly?

---

