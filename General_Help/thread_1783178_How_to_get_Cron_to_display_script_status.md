---
title: "How to get Cron to display script status"
date: 2011-06-15
forum: General Help
---

### Post by skyer2000 on 2011-06-15
Right now I have a cron setup that works. It runs a rsync backup of my server with no issues. However, the backup runs in the background, which is not helpful because sometimes I like to look through the output of rsync for suspicious files or activity.

Running the rsync command manually produces the output I want in the terminal.

Here is what the cron looks like:

0 4 * * * sh /home/user/script.sh

How do I change that so it displays the script status in the terminal?

---

### Post by oldfred on 2011-06-15
I do not know bash well, others will know how to output directly to terminal I think.

But I have saved some links to how to save to log files which is an alternative.

I think these are primarily discussing other issues but show log files in scripts.
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)

Or I copied this from a post:
SOURCE="/home/chris/Music/"
DEST="/media/internal/Media/Music"
LOGFILE="/home/chris/logs/rsync_music2server.txt"

rm -rf $LOGFILE
rsync -auz --log-file=$LOGFILE $SOURCE $DEST
echo "Music backup Done - log file is $LOGFILE"

---

### Post by Dave_L on 2011-06-15
Redirect the script's output to a file:

```
0 4 * * * sh /home/user/script.sh >/home/user/script.log 2>&1
```

To monitor the output as the script is running:

```
tailf /home/user/script.log
```

---

### Post by skyer2000 on 2011-06-15
Outputting to a log file and monitoring it with tailf works perfectly. Thank you!

---

