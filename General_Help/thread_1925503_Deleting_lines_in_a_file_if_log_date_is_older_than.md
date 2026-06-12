---
title: "Deleting lines in a file if log date is older than 1 month old"
date: 2012-02-14
forum: General Help
---

### Post by Jguy on 2012-02-14
I currently have the following bash file, who's job is to update an SVN repository on disk, output the revision number, output the revision data (what changed, by who, revision number, date, etc), update some MySQL databases from the updated content, echo "MySQL updated" and then stop.

```
#!/bin/bash

date
cd /var/www/database/svn
svn up
svn log -r HEAD .
svn log --xml --verbose -r HEAD . > /var/www/database/include/svn.xml
cd sql-files/
mysql -u"user" -p"pass" database < item_db.sql
mysql -u"user" -p"pass" database < mob_db.sql
mysql -u"user" -p"pass" database < mob_skill_db.sql
mysql -u"user" -p"pass" database < item_db_re.sql
echo "Updated MySQL databases..." && echo
cd ~


```

The log outputs:

```

Tue Feb 14 14:04:41 MST 2012
At revision 15581.
------------------------------------------------------------------------
r15581 | user | 2012-02-14 08:29:00 -0700 (Tue, 14 Feb 2012) | 1 line

Removed deprecated memory manager macros (follow-up to r14916).
------------------------------------------------------------------------
Updated MySQL databases...

Tue Feb 14 14:35:12 MST 2012
At revision 15582.
------------------------------------------------------------------------
r15582 | user | 2012-02-14 14:13:54 -0700 (Tue, 14 Feb 2012) | 1 line

Fixed typo in startup script.
------------------------------------------------------------------------
Updated MySQL databases...

```

This is fine and dandy, it runs in a cron with the following command

```

/var/www/database/chksvnup.sh >> /var/www/database/include/log.txt

```

I would like to add some automatic log file management to this script, so that it is capable of cleaning itself up. I don't need a 150KB+ logfile sitting around, but I'd like to keep some data.

I know I'm going to have to use sed for it, I'm just not sure where to start. I want to delete everything in my log file that grows more than 2 months old, by matching the date appended to the file by the bash script and deleting all the lines before that date to the beginning of the file, to make sure it pretty much stays around X amount of KB. Can someone help me out with this? It's a bit out of my league as I've never gotten into bash scripting that much >.<

Thank you in advance for your kind assistance.

---

### Post by SeijiSensei on 2012-02-14
Use logrotate.  Create a root-owned file in /etc/logrotate.d/ containing this configuration:

```
/var/www/database/include/log.txt {
    weekly
    rotate 4
}
```

This will rename log.txt to log.txt.1 each week and keep log.txt.1 through log.txt.4 deleting any older versions.  See "man logrotate" for more details.

---

### Post by Vaphell on 2012-02-14
if you want to do it manually:
USian date format sucks, end of story. If you had all dates in year->month->day->hours->minutes->seconds all digits (like you have in that pseudotable) it would be trivial (awk oneliner would do) because you would be able to simply compare strings alphabetically and the relation between dates would be preserved. Switching months and days around, putting year at the far end and using text complicates things a lot.
In current form you need to fiddle with the date to transform it to unambiguous format to evaluate the relation. Can be done but definitely less pleasant than whipping up a oneliner.

try this
```
#!/bin/bash

regex='^[A-Z][a-z]{2} [A-Z][a-z]{2} [0-9]{1,2} [0-9]{2}:[0-9]{2}:[0-9]{2} [A-Z]+ [0-9]{4}$'

threshold=$( date -d '2 months ago' '+%s' )

skip=true
> trimmed_log.txt

while read line
do
  if [[ $line =~ $regex ]]
  then
    d=${line# }
    d=$( date -d "$d" '+%s' )
    
    if(( d>threshold ))
    then
      skip=false
      echo entry found: "$line"
    else
      echo entry found: "$line (ignored)"
    fi
  fi
  
  if $skip
  then
    continue
  else
    echo "$line" >> trimmed_log.txt
  fi
done < log.txt

echo
echo trimmed_log.txt:
echo =================================
cat trimmed_log.txt
```

---

