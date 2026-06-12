---
title: "rsync log file with data"
date: 2011-07-01
forum: General Help
---

### Post by EECGeek on 2011-07-01
I have successfully backed up my files using a script to a remote server with a log file output.

However the log file is appended each time.

I wish to have a different log file each time with date and time and have yet to figure that part out.

Any help would be great.

---

### Post by gmargo on 2011-07-01
You should show your script.

Here's a simple bit of shell script to generate a nice timestamped filename.  Adjust as needed.
```

#!/bin/sh

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
OUTDIR="."
OUTPREFIX="log_"
OUTSUFFIX=".txt"
OUTFILE="${OUTDIR}/${OUTPREFIX}${TIMESTAMP}${OUTSUFFIX}"

echo "$OUTFILE"

``````

$ ./output_file_with_date.sh
./log_20110701_122900.txt

```

---

### Post by EECGeek on 2011-07-01
Thank you very much, that worked great!!

Heres my script:

#!/bin/sh

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
OUTDIR="/media/data/Backups/Scripts/Logfiles/server"
OUTPREFIX="rsync_log_"
OUTSUFFIX=".txt"
OUTFILE="${OUTDIR}/${OUTPREFIX}${TIMESTAMP}${OUTSUFFIX}"

echo "Preparing to backup in 5 seconds"
sleep 5

rsync -azv --progress --stats --exclude-from="/root/rsync_exclude.txt" --log-file="$OUTFILE" -e ssh /media/data/ ###@########.net:

Any critique you might have would be great!

My next endevor would be to have this log emailed to me after every nightly backup!

---

