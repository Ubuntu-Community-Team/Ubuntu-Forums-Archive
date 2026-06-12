---
title: "how to write tar script so it updates the date automatically..."
date: 2009-07-12
forum: General Help
---

### Post by GMachine_24 on 2009-07-12
Hi:

I've been trying to figure this out and after many hours and man and info pages I still can't work it out.

I want to write a script to run every day to back up my comp using tar. I have the script written but what I need is to add the date automatically each day to the back up name so the script won't cause the tar file to overwrite itself every day.  In other words, I get a new backup tar.gz file every day with a date. (OK, so I guess this means I don't have the script file written yet.)

This is what I have so far:

```

#!/bin/bash


sudo=***** tar -czvf /media/120GB/tarbackup/PIII_fullbackup.tar.gzp  --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/drivesdc1 --exclude=/home/erikm/Desktop --exclude=/control~ --exclude=/sys /


```

I need to inset the date into the PIII_fullbackup.tar.gz file name. So it would be something like 

```


PIII_fullbackup.7.12.09.tar.gz


```


Thanks.

GM

---

### Post by iponeverything on 2009-07-12
```
sudo=***** tar -czvf /PIII_fullbackup.`date +%m.%d.%y.`tar.gz --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/drivesdc1 --exclude=/home/erikm/Desktop --exclude=/control~ --exclude=/sys /
```

---

### Post by entropy1 on 2009-07-12
Have you considered Simple Backup (search for sbackup in synaptic)?

---

### Post by GMachine_24 on 2009-07-12
Ipon: Thanks. You know, I swear I tried that format.... but kept getting error messages. Obviously, however, I did not have it right. Thanks again.

And...

I have not considered Simple Backup . . . but I'll take a look. Thanks for the suggestion.

GM

---

