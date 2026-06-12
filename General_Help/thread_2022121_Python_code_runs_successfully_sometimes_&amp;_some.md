---
title: "Python code runs successfully sometimes &amp; sometimes not"
date: 2012-07-10
forum: General Help
---

### Post by Aqil on 2012-07-10
I wrote a simple script in Python logging activity. It runs great when I start it in Geany, and it seems to be no problem when it is run in the terminal. But when I run without opening the terminal it works sometimes and sometimes not.

```
#!/usr/bin/env python

import subprocess, time
from time import localtime, strftime

try:
	with open('ActivityLog.txt') as f: pass
except IOError as e:
	f=open("ActivityLog.txt", "a")
	f.write("year \t month \t day \t weekday \t hour \t minute \t second \t active window \t idle time \n")
	f.close()

while True:
	try:
		year=strftime("%Y", localtime())
		month=strftime("%b", localtime())
		day_of_the_month=strftime("%d", localtime())
		weekday=strftime("%a", localtime())
		hour=strftime("%H", localtime())
		minute=strftime("%M", localtime())
		second=strftime("%S", localtime())
		activity_var_1=subprocess.check_output("wmctrl -lp | grep `echo $(xprop -root | grep _NET_ACTIVE_WINDOW | head -1 | awk '{print $5}' | sed 's/,//' | sed 's/^0x/0x0/')`", shell=True)
		activity_tuple_1=str.partition(activity_var_1, "   ")
		activity_var_2=str.replace(activity_tuple_1[-1],"\t", " ").strip("\n")
		activity_tuple_2=str.partition(activity_var_2, " ")
		activity_var_3=activity_tuple_2[2]
		idle_var=subprocess.check_output("xprintidle", shell=True)
		f=open("ActivityLog.txt", "a")
		f.write(year + "\t" + month + "\t" + day_of_the_month + "\t" + weekday + "\t" + hour + "\t" + minute + "\t" + second + "\t" + activity_var_3 + "\t" + idle_var)
		f.close()
		time.sleep(2)
	except IOError as e:
		f=open("ActivityLog.txt", "a")
		f.write("Logging the data failed")
		f.close()
		time.sleep(2)


f=open("ActivityLog.txt", "a")
f.write("The loop was skipped!")
f.close()

# wmctrl must be installed
# xprintidle must be installed

```

I double click the file and click on run. When it works, it's writing to the log file as I want it to. The output in ActivityLog.txt is something like this

```
year 	 month 	 day 	 weekday 	 hour 	 minute 	 second 	 active window 	 idle time 
2012	Jul	10	Tue	15	06	54	ActivityLogger	175
2012	Jul	10	Tue	15	06	56	ActivityLogger	2212
2012	Jul	10	Tue	15	06	58	ActivityLogger	4248
...
2012	Jul	10	Tue	15	14	18	Ubuntu Forums - Post New Thread - Chromium	48
2012	Jul	10	Tue	15	14	20	Ubuntu Forums - Post New Thread - Chromium	132
2012	Jul	10	Tue	15	14	22	Ubuntu Forums - Post New Thread - Chromium	382
```

When it fails, no error appears. It writes the part before the loop but after that nothing happens. Output then looks like this:

```
year 	 month 	 day 	 weekday 	 hour 	 minute 	 second 	 active window 	 idle time 
```

Same thing happens when the script is run automatically on startup using the startup applications feature in ubuntu 11.10 but the log file is then written in /home/aqil/ instead of /home/aqil/subfolder .

When it works it is available as a process in htop and it's using very little CPU and memory. When it's not working I can't find it in htop.

It doesn't seem to matter whether the file exists or not when I run the script. It can fail and then succeed the next time I try a few seconds later without having changed anything.

Why is this happening and what can I do to fix it?

---

