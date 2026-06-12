---
title: "Clamav Bash Script"
date: 2011-12-10
forum: General Help
---

### Post by tomkadwill on 2011-12-10
I wrote a little bash script, which I have then automated with cron, to scan my home directory. Perhaps it might help someone. 

```
#!/bin/bash

sudo notify-send ClamScan "Beginning Scan"
sudo /usr/bin/freshclam
sudo cp /dev/null /var/log/clamav/clamscan.log
sudo /usr/bin/clamscan -r --exclude-dir=/home/tom/SVN --log=/var/log/clamav/clamscan.log /home/tom
sudo gedit /var/log/clamav/clamscan.log
sudo notify-send ClamScan "Scan Complete"

```

1) The script notifies the user with a notification bubble when the scan begins.
2) Updates the clamav database
3) Empties the log file (you would need to create this first)
4) Scans the home directory, excluding my SVN folder and outputs the results to clamscan.log.
5) Opens the log file
6) notifies the user that the scan is complete.

---

