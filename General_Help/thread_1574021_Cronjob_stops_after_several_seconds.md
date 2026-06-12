---
title: "Cronjob stops after several seconds?"
date: 2010-09-13
forum: General Help
---

### Post by baustromverteiler on 2010-09-13
Hi,

I want to use a cronjob to start a script running streamripper to record radioshows when I'm not at home. I'm running 10.04 server 32 bit.

I've setup a cronjob via Webmin to start the recording. It runs the following script: 

```

ORDNER=`date +%Y"_"%m"_"%d"-"%H"_"%M"(FM4)"` # 'ORDNER' means Folder and creates a folder with time/date to save the stream
streamripper http://mp3stream1.apasf.apa.at:8000/ -d /mnt/Samsung/Radio/$ORDNER --xs_padding=2000:500 -a -q -s 

```

The script is started by the crojob as expected (I checked with ps -A | fm4) but the script suddenly stops running after aproxx. 15 seconds.

there's nothing in the syslog file except a line telling the cronjob started.

```
Sep 13 22:01:01 Datenscheune CRON[6476]: (root) CMD (/home/max/Desktop/Radioscripts/./fm4 #Aufnahme FM4)
```

Is there any logfile or way to see why the script is killed or what stops the recording? When executing the script manually the recording runs just fine until I kill the process.

regards, max

---

### Post by baustromverteiler on 2010-09-13
I'm afraid I'm missing something obvious here ... 

when I pipe the output of the script to a textfile with

```
/home/max/Desktop/Radioscripts/./fm4 > /home/max/Desktop/ac.txt   
```

everything works as expected, the script keeps running until another cronjob kills it ...

please enlighten me!

---

### Post by Gunman1982 on 2010-09-13
When the script runs through cron it doesn't have the full PATH variable set. Try to use absolute paths for the programms date and streamripper to be sure. Or set the PATH variable in your script.

(locate date / locate streamripper)

---

