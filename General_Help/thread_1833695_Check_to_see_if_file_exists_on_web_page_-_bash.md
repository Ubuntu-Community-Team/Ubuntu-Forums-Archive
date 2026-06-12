---
title: "Check to see if file exists on web page - bash"
date: 2011-08-26
forum: General Help
---

### Post by CorpusWolf on 2011-08-26
I am trying to write a bash script to download a file from a web page. The file need only be downloaded if it has been uploaded, running the script and allowing it to fail fills my error logs with misc info. What i have so far checks to see if the file has already been downloaded and if not attempts to download file, I'd like another check to see if the file is on the website before it makes the attempt. Already have it set up in crontab to run at specified times.

Running Ubuntu 10.04

Code I have so far:

```
# !/bin/bash
#
# Download files which do not use RSS
#
# Set Variables
YEAR=`date +%Y` #YYYY
year=`date +%y` #YY
MONTH=`date +%m`
DAY=`date +%d`
TODAY=`date +%Y%m%d`
#
#Download Files
# DN Headlines in Spanish
if [ ! -f /home/radiobackup/DNHeadlinesESP/dn$YEAR-$MONTH$DAY-es.mp3 ]; then
cd /home/wazu/radiobackup/DNHeadlinesESP/
wget http://distro.democracynow.org/dn${YEAR}-${MONTH}${DAY}-es.mp3
# Move to import folder
cp /home/wazu/radiobackup/dn$YEAR-$MONTH$DAY-es.mp3 /home/wazu/radiodropbox/DNHeadlinesESP/dnheadlinesesp$TODAY
fi
```

---

### Post by aeiah on 2011-08-26
easiest thing to do would probably be to just use the quiet flag (-q) so you dont get output at all.

you could also take influence from [this page]("http://www.commandlinefu.com/commands/view/2871/use-wget-to-check-if-a-remote-file-exists"). i used the alternative from that page.. basically it checks if file exists, and if it does it downloads it, and copies it. if it does not exist it just says 'file does not exist'

```

# !/bin/bash
#
# Download files which do not use RSS
#
# Set Variables
YEAR=`date +%Y` #YYYY
year=`date +%y` #YY
MONTH=`date +%m`
DAY=`date +%d`
TODAY=`date +%Y%m%d`
#
#Download Files
# DN Headlines in Spanish
if [ ! -f /home/radiobackup/DNHeadlinesESP/dn$YEAR-$MONTH$DAY-es.mp3 ]; then
cd /home/wazu/radiobackup/DNHeadlinesESP/




wget -O/dev/null -q http://distro.democracynow.org/dn${YEAR}-${MONTH}${DAY}-es.mp3 && wget http://distro.democracynow.org/dn${YEAR}-${MONTH}${DAY}-es.mp3 && cp /home/wazu/radiobackup/dn$YEAR-$MONTH$DAY-es.mp3 /home/wazu/radiodropbox/DNHeadlinesESP/dnheadlinesesp$TODAY || echo file does not exist


fi

```

---

### Post by CorpusWolf on 2011-08-26
I still need any actual errors to be reported, just not that it fails because the file hasn't been uploaded yet

---

