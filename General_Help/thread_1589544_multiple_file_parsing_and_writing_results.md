---
title: "multiple file parsing and writing results"
date: 2010-10-06
forum: General Help
---

### Post by TDrakeHI on 2010-10-06
Ok,

I am currently using rsync to do an offsite backup of my user profiles to my webserver, and have been doing this for over a year and in auditing the backup I am noticing an anomaly that appears periodically, but to be able to further root it out I need to process over 400 log files.  Now, the information I am looking for is always in the last 4 lines of the log file and so I would like to write a script that would pull the last 4 lines of all the logs and write them into a separate file.  This to me sounds incredibly simple, but I don't know enough about script programming to be able to do this.  Does anyone have any tips or a direction to point me to get the info I need.  I like writing code, but just haven't done enough of it.

Thanks in advance for any help given.

Tim Drake

---

### Post by papibe on 2010-10-06
Assuming all logs are on one directory, and their file names match *.log, something like this could help you:
```
#!/bin/bash
for file in *.log
do
    echo "$file:" >> auditing
    tail -n 4 "$file" >> auditing
done

```
The file auditing will have 5 lines per log. First one will be the name of the log, and the 4 left will be that log's last 4 lines.

Good Luck.

---

### Post by TDrakeHI on 2010-10-06
That did it.  Thank you very much

---

