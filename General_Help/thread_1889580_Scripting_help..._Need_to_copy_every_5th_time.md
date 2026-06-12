---
title: "Scripting help... Need to copy every 5th time"
date: 2011-12-01
forum: General Help
---

### Post by Tralce on 2011-12-01
So I'm using the command line utility "webcam" to save frames from a camera to a folder in /var/www for remote viewing, but I also want to save frames. The files range from 2k to 20k. One frame per second is saved. I have the following script running the camera.
```
#!/bin/sh
webcam /etc/cam/webcamrc & # saves 1 frame per second
while :
do
	convert /var/www/[redacted]/outdoor.jpg -resize 50% /var/www/[redacted]/outdoor_sm.jpg #smaller, 320x240 copy
	if [ ! -d "/home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H)" ]
	then
	       mkdir -p /home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H) #copy it to a folder year/month/day/hour if that exists, otherwise make it
	fi
	cp /var/www/[redacted]/outdoor_sm.jpg /home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H)/outdoor-$(date +%Y.%m.%d.%H.%M.%S).jpg #and make sure it's named year.month.day.hour.minute.second.jpg
	sleep 0.75 #this takes 250ms on this system so sleep for the rest of the second
done 
```

Now this is all great but MAN do these files stack up. A day directory ranges from 500 to 1000MB. So, I want to modify my script to save every nth frame taken. Preferably 5th. For security reasons. Maybe one every 20 seconds. Who knows. How would I go about doing that? I was thinking a for loop somehow but I just can't seem to make it work.

---

### Post by mutley89 on 2011-12-01
Would something like this work?:
```

count=0
while true
do
  stuff to do every time
  let count++
  if [[ $count -eq 5 ]]
  then
    stuff to do every fifth time
    count=0
  fi
done

```

---

### Post by Tralce on 2011-12-01
Awesome, dude! Perfect idea. It works! 

```
#!/bin/bash
webcam /etc/cam/webcamrc &
counter=0;
while :
do
	convert /var/www/[redacted]/outdoor.jpg -resize 50% /var/www/[redacted]/outdoor_sm.jpg
	let "counter += 1";
	if [[ $counter -eq 5 ]]
	then 
		if [ ! -d "/home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H)" ]
		then
		       mkdir -p /home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H) 
		fi
		cp /var/www/[redacted]/outdoor_sm.jpg /home/[redacted]/security/$(date +%Y)/$(date +%m)/$(date +%d)/$(date +%H)/outdoor-$(date +%Y.%m.%d.%H.%M.%S).jpg 
		counter=0;
	fi
	sleep 0.75 
done 
```

Done and done.

---

### Post by btindie on 2011-12-01
If you fancy experimenting you could achieve something very similar using some standard tools.

Incrond which you can use to monitor a directory so that when a new file is created it triggers a bash script which then resizes etc..

To handle all of the files you could use logrotate which is generally used for log files but it can hanndle files of any type. If that doesn't fit your needs enough then just create a regular cron hourly/daily job to archive your files.

You can then just leave it be and not worry if your script is running or not.

---

