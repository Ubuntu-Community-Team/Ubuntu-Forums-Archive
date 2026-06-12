---
title: "torrents &amp; virusses"
date: 2009-10-10
forum: General Help
---

### Post by mrkazoodle on 2009-10-10
hi

Since I'm still using windows I'd like to scan my files after they're downloaded. I'd like to do this automatically, so I'm looking for a solution to run a terminal command to scan the file after it has downloaded.
Currently I'm using Deluge, I've found an '[Execute plugin]("http://dev.deluge-torrent.org/browser/trunk/deluge/plugins/execute?rev=5217")', but I think it's still in development.
I hoped you guys might have a solution for this problem.

(on my ubuntu I've got BitDefender and Avast. I use them to scan my windows when it has gotten infected, has happened once last year)

---

### Post by nikhilbhardwaj on 2009-10-10
try clam antivirus

---

### Post by mrkazoodle on 2009-10-10
> **nikhilbhardwaj said:**
> try clam antivirus

it's not the antivirus program that's the problem,
it's the torrent program that needs to start the scanner when it finishes downloading a file

---

### Post by nikhilbhardwaj on 2009-10-10
sorry
didn't see that

don't know bout that

---

### Post by OpenGuard on 2009-10-10
Avast can do that easily - install and read it's man page .. you can initiate a scan on a specific folder or file via command line.

---

### Post by mrkazoodle on 2009-10-11
> **OpenGuard said:**
> Avast can do that easily - install and read it's man page .. you can initiate a scan on a specific folder or file via command line.

I'm looking for _a torrent proram that starts the scanner automatically_, not an antivirus program

---

### Post by blueridgedog on 2009-10-11
The best solution that jumps to my mind is to use your favorite torrent application and to install ClamAV.  Configure ClamAV to scan the "save to" directory of your on time basis that suits you (every 30 minutes, every hour, every 2 hours...whatever).

---

### Post by orky7 on 2009-10-11
automatically u cant do it..... but yes u can set the time to scan a folder as u like in clamAv

---

### Post by Boondoklife on 2009-10-11
I would not say you cant do it automatically, you could use transmission and transmission-remote in a script and put that in a cron job to monitor the status of your torrents. Once it sees one as done you can have it stopped and do what ever you wish.

I use something very similar in a download appliance I have, and use it to manage the starting and stopping of torrents automatically. If you take the time to write the script then you can do almost anything.

Here is the script I use so you have a base to start from:```

#!/bin/sh

echo "Starting Check transmission"

# *************
# Maximum number of torrents that may be active at any given time
MAXACTIVE="3"
FORCELIMIT="0"
REMOVEFINISHED="0"

echo `date`

# Add a quick check to see if another check is running
if [ -f /tmp/checktransmission ]; then
    echo "Already running!"
    exit
fi
/bin/touch /tmp/checktransmission

# Path to transmission-remote
REMOTE="/opt/bin/transmission-remote"

# *************
# Stop all finished torrents
echo "Searching for Finished Torrents"
LIST="$($REMOTE -l | tail -n +2 | grep 100% | grep -v Stopped | awk '{ print $1; }')"
for ID in $LIST; do
    NAME="$($REMOTE --torrent $ID --info | grep Name:)"
    echo "Stopping $ID: ${NAME}"
    $REMOTE --torrent $ID --stop >/dev/null
done

if [ $REMOVEFINISHED -eq 1 ]; then
    # Remove all finished torrents
    LIST="$($REMOTE -l | tail -n +2 | grep 100% | grep Done | grep Stopped | awk '{ print $1; }')"
    for ID in $LIST; do
        NAME="$($REMOTE --torrent $ID --info | grep Name:)"
        echo "Removing $ID: ${NAME}"
#       echo -e "${NAME#*Name: } >>> finished on `date`\n\r" >> /shares/internal/public/finished_torrents.txt
        $REMOTE --torrent $ID --remove >/dev/null
    done
fi


# How many are still running?
echo "Counting Active Torrents"
ACTIVE="$($REMOTE -l | tail -n +2 | grep -v Stopped | grep -v Sum: | wc -l)"
echo "$ACTIVE Found:"
if [ $ACTIVE -gt $MAXACTIVE ]; then
    if [ $FORCELIMIT -eq 1 ]; then
        # Stop any torrents above the queue limit - ie ONLY download the MAXACTIVE at a time, no matter whether they are started manually
        LIST="$($REMOTE -l | tail -n +2 | grep -v Stopped | grep -v Sum: | tail -n $(expr $ACTIVE - $MAXACTIVE) | awk '{ print $1; }')"
        for ID in $LIST; do
            NAME="$($REMOTE --torrent $ID --info | grep Name:)"
            echo "Force Stopping $ID: ${NAME}"
            $REMOTE --torrent $ID --stop >/dev/null
        done
        /bin/rm /tmp/checktransmission
        exit
    fi
    if [ $FORCELIMIT -eq 0 ]; then
        /bin/rm /tmp/checktransmission
        exit
    fi
fi

# Start new torrents
echo "Starting Torrents"
LIST="$($REMOTE -l | tail -n +2 | grep -v 100% | grep Stopped | head -n $(expr $MAXACTIVE - $ACTIVE) | awk '{ print $1; }')"
#echo "$LIST"
for ID in $LIST; do
    NAME="$($REMOTE --torrent $ID --info | grep Name:)"
    echo "Starting $ID: ${NAME}"
    $REMOTE --torrent $ID --start --verify >/dev/null
done

echo "Check transmission Done"
/bin/rm /tmp/checktransmission

```* NOTE: I did not write this but have modified it to suit my purposes.

---

### Post by Johnny B on 2009-10-11
for this script you need [conkydeluge]("http://ubuntuforums.org/showthread.php?t=946664")


adapted from [here]("http://ubuntuforums.org/showthread.php?t=1220675")
```
#!/bin/bash
DL=`conkyDeluge |grep Downloading`
while [ "$DL" != "" ] ;do
DL=`conkyDeluge |grep Downloading`
# echo "not yet"
sleep 10
done

clamscan $torrent_folder
 
```

---

