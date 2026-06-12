---
title: "Location of CUPS Completed Jobs Logfile?"
date: 2009-10-13
forum: General Help
---

### Post by dbsoundman on 2009-10-13
I'm trying to find out where CUPS stores the list of completed jobs that is viewable through the web interface at localhost:631/cups. Basically I want to be able to import this data into a spreadsheet so I can track printer usage from various users. Any help would be appreciated!

Thanks,
Dan

---

### Post by wojox on 2009-10-13
Depends my Hp will log to /var/log/cups/page_log but my Brother printer won't log at all.

---

### Post by dbsoundman on 2009-10-30
I finally figured out what I wanted to do. I searched around a bit for some way to log the print data in such a way that I could use it to tabulate printer usage by user, and I found this: [http://savannah.nongnu.org/projects/printanalyze/]("http://savannah.nongnu.org/projects/printanalyze/"). It's a really nice little script that reads the CUPS print_log and sorts the data all sorts of ways. I set up a cron job (command: crontab -e) which ran this program (PrintAnalyzer) as sudo and wrote the output to a file called print.log. So my crontab entry looks like:
```
00 * * * * sudo PrintAnalyzer > ~/print.log
```. (If you're unsure what the 00s and stars do at the beginning, check out [this helpful page]("http://www.tech-faq.com/create-cron-job.shtml").) 

Finally, I created a script called printlogarchive, which I use to archive the print.log at the end of each month. (PrintAnalyzer does show cumulative data, so the hourly overwrites still show the previous print job info, but I wanted to have a per-month log as well.) The script is like this:
```

#!/bin/bash
dt=$( date +%y%m%d.%k%M )
mv print.log print_${dt}.log
mv print_${dt}.log ~/printlog_archive/

```
where "dt" is a variable of sorts built by the command "date", which in this case sets up a string with the two-digit year, month, and day, a ".", then the 24-hour time and minute. I added "printlogarchive" to the crontab as well, setting it to run once a month.

(I should also note that both of my scripts were moved to /usr/local/bin/ once they were finished so that they were executable from the command line without having to be in their directory and type a "./" in front of the command. And of course the file permissions were changed so that the file is executable.)

I tried to make this info newbie-friendly so that others can use this info, but let me know if you have questions!

-Dan

---

