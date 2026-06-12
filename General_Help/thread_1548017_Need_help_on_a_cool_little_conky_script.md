---
title: "Need help on a cool little conky script"
date: 2010-08-07
forum: General Help
---

### Post by sideaway on 2010-08-07
Hey there, I'll try explain what I'm trying to do.

I have a torrent server running Deluge that downloads Pioneer one and other assorted shows using Flexget, and then consequently saves the downloaded shows in 
```

/media/Toms/Torrent_Server/Series/%(series_name)s/Season %(series_season)d/
```
on the server. The HDD 'Toms' is a one terrabyte storage drive for remote backups and newly downloaded media. Its IP is permanaently 192.168.1.6, as shown in the rsync command below.

at 8am every morning (deluge downloads from 2am - 8am every day) I have a cron job run an rsync command that updates the local folder (/media/TV) on my computer

```
rsync -ravue ssh server@192.168.1.6:/media/Toms/Torrent_Server/Series/ /media/TV
```
I have run "ssh-keygen -t rsa" in order to allow passwordless access between my desktop and server.

Now the hard part - I'd like a conky that displays the recently copied episodes perhaps for 2 or 3 days. And I have no idea how to do it... can someone help me? If I can get this going, I have a backup rsync running in the other direction and I'd like the conky to display recently backup files and perhaps even the date/time my directories were last backed up.

I use rsync for backing up as I find it handles ssh much better than any of the GUI solutions.

---

