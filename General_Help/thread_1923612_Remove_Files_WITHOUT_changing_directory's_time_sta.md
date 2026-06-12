---
title: "Remove Files WITHOUT changing directory's time stamp"
date: 2012-02-11
forum: General Help
---

### Post by Kissell on 2012-02-11
We keep a folder for certain data that contains copies of just recent files, things from the last week or so... anything that hasn't been edited or created in that time gets removed, because there is a backup copy in permanent archival storage, but we just wanted the folder to be lean and clean for daily usage.  

So I run a cron job like this:
> /usr/bin/find "/media/Data/Recent Files" -mtime +7 -exec /bin/rm {} -R \;


It works great, but there are many subfolders in Recent Files and when it deletes a file it changes the sub folder's date...  which is undesirable...  

Inside the Recent Files directory, I might sort the folder by date, so I can see the most recently modified, but every day when this script runs if it deletes a file it changes that sub folder's date stamp, making it appear higher on the list in date sorted order than I would like...  

Basically, I don't want "rm" to change the directory date and time stamp...  

Is there a way to do this?

---

### Post by Kissell on 2012-02-11
This is what I started with...  I was trying to modify the cron job to save the time stamp, then delete the files, the use "touch" to restore the time stamp to the directories...  I got about this far and then thought there has to be a solution out there already.

> 
/usr/bin/find "/media/Data/Recent Files" -mtime +7 -exec stat -c %y {} \; | cut -d '.' -f1|sed s/-//g|sed s/://|sed 's/ //g'|cut -d ":" -f1


BTW: I was trying to do this all from cron without writing a script and having to have yet another special file...  but it looks like I might have to go the bash scripting route, unless there's an easier way.

---

