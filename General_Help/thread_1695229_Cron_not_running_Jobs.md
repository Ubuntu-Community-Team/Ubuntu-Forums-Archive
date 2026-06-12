---
title: "Cron not running Jobs"
date: 2011-02-25
forum: General Help
---

### Post by gavinjb on 2011-02-25
Hi,

Just trying to run my Wallpaper Changer script as a Cronjob, but cron doesn't appear to be running the script, the path in the script is the full path to the wallpaper folder (e.g. /home/user/Pictures...)

Also the path to the script in the cronjob is the full path, I have also tried to look for the cron log file and Ubuntu doesn't seem to be generating one (or at least it doesn't exsit in /var/log where I would expect it)

Incase for some reason Cron isn't starting I thought I would try stopping and then starting cron, but when I try to Start, Stop or Restart cron I get the following error

```

sudo cron stop
cron: can't lock /var/run/crond.pid, otherpid may be 1310: Resource temporarily unavailable

```

Can anyone help?

Thanks,


Gavin,

---

### Post by CharlesA on 2011-02-25
You manage cron by running this:

```
sudo service cron stop|start|restart
```

By default cron emails any errors, so you'd need a MTA installed (Exim of Postfix), or redirect the error output to a file.

---

### Post by gavinjb on 2011-02-25
Thanks, I can confirm that cron was running all along but for some reason my jobs are failing to start, but if I run what cron should be running manually then there is no problem, any ideas?

below is my crontab -l

```

crontab -l
*/5 * * * * /media/Gavin/Documents/Scripts/ChangeWallpaper.sh  > /home/Gavin/cw.log # JOB_ID_3
5 * * * * /home/Gavin/Document/Script/backup.sh # JOB_ID_4

```

the log file I am trying to generate to see what the error is, is not even giving me an log file.

there isn't anyway of getting cron to generate a generic error file instead of trying to output to mta as I dont want to goto the hasle of installing an MTA and doing any configuring just to get my cron jobs working and then removing it.


Thanks,


Gavin,

---

### Post by CharlesA on 2011-02-25
Is your home directory encrypted?

You can try Running this:

```
*/5 * * * * /media/Gavin/Documents/Scripts/ChangeWallpaper.sh > /tmp/cronlog 2>&1
```

---

### Post by gavinjb on 2011-02-25
Hi,

I just realised that I had missed the sharepoint in the path so I had /media/Gavin/... instead of /media/Data/Gavin/...

After adding that I get the log file created, but the script doesn't seem to be running correctly.

I have added a couple of echo statements to my script to see if I can find why the script isn't running corectly, but when I look at the cronlog both the echo statements are running!

Script that should be running, when I run this manually it works fine
```

#!/bin/bash

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/media/Data/Gavin/Pictures/Other/Set1"
echo "Wallpaper Changer" 

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)
echo $PIC
# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

echo "completed"

```

PS: my home dir is not incrypted, but I do have my data stored on a different partition and the folders (e.g. Pictures, Documents...) are symlinked back

---

### Post by CharlesA on 2011-02-25
The logs should include any error output as well.

---

### Post by gavinjb on 2011-02-26
the log seems to be overwritten after each run, below is a copy of what I get in the log

```

Wallpaper Changer
/media/Data/Gavin/Pictures/Other/Set1/leaning_1024.jpg
completed

```

---

### Post by CharlesA on 2011-02-26
Try using the full path to gconftool

---

