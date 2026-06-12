---
title: "Help with Cron job"
date: 2010-10-14
forum: General Help
---

### Post by Wackey on 2010-10-14
I am trying to get a cron job to work.
This i what i done: 
Í have make a sh file witch i name jeff.sh the file contain: 

#!/bin/bash 
find /usb/sda1 -mtime +3 -exec rm {} \; 
cd /usb/sda1 
mv upload `date +%m.%d.%Y` 
mkdir upload 
chmod 777 upload 

The file is save in /etc/cron.d/ 

In /etc/cron.d/root i have add the line 
0 * * * * /etc/cron.d/jeff 
to get the script to run. 

but nothing happen :( 

To explain what iam trying to do.
my ipcam send picture to the folder upload.
every hour i will have cron to:
1. rename the folder upload with the day and time
2. create a new folder upload
3. make the new folder write for all
4. check if there are any folder/files there are older the 3 days, if there are delete them.

can sombody help me?

---

