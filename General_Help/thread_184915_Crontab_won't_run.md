---
title: "Crontab won't run"
date: 2006-05-30
forum: General Help
---

### Post by sjitan on 2006-05-30
I need helping getting this script to run every five minutes.
The cron job won't execute and I don't know why.  I've tested other cron jobs and they work fine.  Please look at the script and please help.  I can execute the script fine from the command line.
crontab entry
5 * * * * /home/xxx/llimage-script

**_llimage-script_**

#!/bin/bash
export emailaddr="xxx@xxxxxxxxx.com [email]xxx1@xxxxxxxx.com[/email]"

export ToDir=/home/xxx/alerts

export MailFile=results.mail

export llimage02_path=/sync/llimage02/$(date +%Y)/$(date +%m | sed -e 's/^0//')/$(date +%d | sed -e 's/^0//')
export llimage03_path=/sync/llimage03/$(date +%Y)/$(date +%m | sed -e 's/^0//')/$(date +%d | sed -e 's/^0//')

if [ -d $llimage02_path ]; then
        echo "Directory '$llimage02_path' exists!!!"
        if [ -d $llimage03_path ]; then
                echo "Directory '$llimage03_path' exists!!!"
                echo "Starting Unison"
        else
                echo "creating '$llimage03_path'"
                mkdir $llimage03_path
                echo "Starting Unison"
        fi
else
echo "Error: '$llimage02_path' does not exist!!"
echo "EXITING"
exit 1
fi

###################################################################

# Sending the mail and/or page to the appropriate parties.        #

###################################################################

#/usr/bin/unison -silent -batch $llimage02_path $llimage03_path -force $llimage02_path > $ToDir/results
/usr/bin/unison -silent -batch $llimage02_path $llimage03_path -force $llimage02_path > $ToDir/results

/bin/grep -i error $ToDir/results > $ToDir/$MailFile
export count=`/usr/bin/wc -l $ToDir/$MailFile | /usr/bin/awk '{print $1}'`

if [ $count != "0" ]
then
/usr/bin/nail -s "xxxxxxxxxxx Production Issue" -c [email]xxx@xxxxxxxxxx.com[/email] error < $ToDir/$MailFile
else
/bin/echo  "Sucess" >> /home/xxx/unilog
fi
rc=$?
if [ "$rc" != "0" ]
then
echo  write_log "ERROR:  Failed to mail alerts to $emailaddr";
fi

---

### Post by kingmonkey on 2006-05-30
> 5 * * * * /home/xxx/llimage-script

This would run every 5 min past the hour. What you want is  */5 * * * *

(All the edits are due to me totally confusing myself)

---

