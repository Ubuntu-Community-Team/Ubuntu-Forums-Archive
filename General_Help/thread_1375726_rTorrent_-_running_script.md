---
title: "rTorrent - running script"
date: 2010-01-08
forum: General Help
---

### Post by Prabas on 2010-01-08
Hello, 
maybe you guys know how to run script when one of my  dowloads completes. For e.g. i want to run "script.sh dir_which_completed" always when any of downloads completes. or somehow to copy that dir to /home/prabas/completed and something writes "script.sh dir_which_added" when new dir is added.

---

### Post by prem1er on 2010-01-08
rTorrent has functionality that allows it to move completed downloads to a new directory. You need to read the documentation.

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrents](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrents)

---

### Post by Prabas on 2010-01-08
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,/home/prabas/downloads/;d.set_directory=/home/prabas/completed/" i added that to rtorrent.rc and tried, and it still on /downloads/ dir

---

### Post by kempy1000 on 2010-01-08
Hi

I had trouble with this before and couldn't find a solution in the .rtorrent.rc file.

So i set up rtorrent completion moving and moved the finished download to a folder (downloaded) and had a detached screen (running as user rtorrent) with a folder monitoring script inside it that ran tvnamer.py (could use any script with the downloaded file as $1) on the downloaded file.

Would this work for your problem? I can post all the steps to set it up if needed.

Chris

---

### Post by Prabas on 2010-01-08
> **kempy1000 said:**
> Hi

I had trouble with this before and couldn't find a solution in the .rtorrent.rc file.

So i set up rtorrent completion moving and moved the finished download to a folder (downloaded) and had a detached screen (running as user rtorrent) with a folder monitoring script inside it that ran tvnamer.py (could use any script with the downloaded file as $1) on the downloaded file.

Would this work for your problem? I can post all the steps to set it up if needed.

Chris

Yes, if you can :) ill try everything, if thats not so hard, because im not experienced with that. If i understand you correctly, it moves file to "downloaded" dir and runs script like "script.sh dir_name" ? if yes or something like that, thats awesome ;)

---

### Post by kempy1000 on 2010-01-08
> **Prabas said:**
> Yes, if you can :) ill try everything, if thats not so hard, because im not experienced with that. If i understand you correctly, it moves file to "downloaded" dir and runs script like "script.sh dir_name" ? if yes or something like that, thats awesome ;)

Thats exactly what it does. Ill write it all up now and post it...

---

### Post by kempy1000 on 2010-01-08
First of all inotify is needed:
```

sudo apt-get install inotify-tools

```

I run rtorrent as user rtorrent.
My download directory is /mediadrive/torrent/downloaded/
I set rtorrent to download to /mediadrive/torrent/inprogress then once the torrent finishes move it to download directory.

These are my scripts the can be adjusted as needed.

/etc/init.d/rtorrentdeamon

This runs on startup to start rtorrent detached in a screen and also starts the monitor

```

 #! /bin/sh

 #executable files in the following paths that are perhaps needed by the script
 PATH=/bin:/usr/bin:/sbin:/usr/sbin

 case "$1" in
 start)
       echo "Starting rtorrent..."
       su rtorrent -c "screen -dmS rtorrentdeamon rtorrent"
       echo "Starting rtorrent monitor..."
       su rtorrent -c "screen -dmS monitor /home/rtorrent/scripts/monitor"
    ;;
 stop)
       echo "Stopping rtorrent...."
       sudo kill -2 `pidof rtorrent`
       echo "Killing monitor..."
       sudo pkill screen
       echo " ... done."
       sudo rm -rf /mediadrive/torrent/session/rtorrent.lock
    ;;
 *)
    echo "Usage: $0 {start|stop}"
    exit 1
    ;;
 esac

 exit 0

```

/home/rtorrent/scripts/monitor

This script watches the MONITORFOLDER for changes.
If a change is detected it:
1) Moves into the MONITORFOLDER
2) Executes tvnamer on the newly downloaded file ($NAME)
```

#!/bin/bash

LOGFILE=/home/rtorrent/scripts/logs/monitorvideos.log
MONITORFOLDER=/mediadrive/torrent/downloaded

exec >> $LOGFILE 2>&1

while [ 1 ]
do
        inotifywait --monitor -q --format %f --event moved_to $MONITORFOLDER | while read NAME
        do
                echo "-----------------------------------------------------------------"
                date
                echo "Moving into $MONITORFOLDER"
                cd $MONITORFOLDER
                echo "Running tvnamer on $NAME"
                sudo tvnamer -b "$NAME" #This is the command that is run 
                echo "-----------------------------------------------------------------"
        done
        sleep 300
done

```

You could just cut this code to the basics....
```

#!/bin/bash

LOGFILE=/home/rtorrent/scripts/logs/monitorvideos.log
MONITORFOLDER=/mediadrive/torrent/downloaded

exec >> $LOGFILE 2>&1

while [ 1 ]
do
        inotifywait --monitor -q --format %f --event moved_to $MONITORFOLDER | while read NAME
        do
              #EXECUTE ME ON FOLDER CHANGE ($NAME is the name of the download)
        done
        sleep 300
done

```

In .rtorrent.rc I have this line to move downloaded files from /mediadrive/torrent/inprogress to /mediadrive/torrent/downloaded
```

system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,/mediadrive/torrent/downloaded/;d.set_directory=/mediadrive/torrent/downloaded/"

```

Hope this helps!

If your setup is very different and your stuck post some details and ill try help more!

E.g:
How you run rtorrent and your directory's

Chris

---

### Post by Prabas on 2010-01-08
[FONT=monospace]system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/completed/;d.set_directory=~/completed/"

What i need to change if i want to copy files, not move?
[/FONT]

---

### Post by kempy1000 on 2010-01-09
> **Prabas said:**
> [FONT=monospace]system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/completed/;d.set_directory=~/completed/"

What i need to change if i want to copy files, not move?
[/FONT]

So did it end up working? My best guess would to change it to:
```

system.method.set_key = event.download.finished,move_complete,"execute=`cp -r`,-u,$d.get_base_path=,~/completed/;d.set_directory=~/completed/"

```

But im not 100% 
cp -r is copy recursively you need the -r if your files are in individual folders or else it will skip the folder.

Chris

---

### Post by Prabas on 2010-01-09
Thank you, everything is working

---

### Post by kempy1000 on 2010-01-09
> **Prabas said:**
> done
sleep 300
done

What that "sleep 300" means? it ignores everything for 300mins or seconds?

It pauses the script for 300 seconds, it allows the program in the loop to finish executing before the watch starts again. You could try removing it but im not sure what will happen.

Chris

---

