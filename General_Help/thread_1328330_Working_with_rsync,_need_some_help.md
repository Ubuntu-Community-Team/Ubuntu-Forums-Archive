---
title: "Working with rsync, need some help"
date: 2009-11-16
forum: General Help
---

### Post by coffee on 2009-11-16
I have a rsync script in Python that is working well for me.  It has 3 files the main backup.py and restformat.py used to formate my title and subtitles in the log file and backupexcluded.txt with the directories I do not what to backup.  I have this setup as a cron job to run everyday

What I would like to end up with is something that checks to see if it is the first run, then asks what to backup and where to put the backup, then creates the directories and files needed in the backup location (the former I think I should have setup in the next couple days).  How do I hold these variables (source, destination, and logfile) in a config file separate from the code and read at run time as apposed to being scripted in the code itself?

I would also like to be able to print the files to be backed up and the files to be moved to *increments* (the files deleted/moved since the last backup).

**_backup.py_**
```
#!/usr/bin/python

import os
from time import asctime
import restformat

#Variables
backupruntime = asctime()
sourcedir = "/home/coffeeboy/"
backupdir = "/media/FreeAgent/backup/"
incrementsdir = '/media/FreeAgent/backup-increments/' + backupruntime

#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.title(backupruntime))
print >> backuplog, ('Making increments directory: "' + incrementsdir + '"\n')

#Make incrementsdir
os.mkdir(incrementsdir)

#Logging
print >> backuplog, (restformat.subtitle('BEGIN BACKUP'))
backuplog.close()

#Run rsync backup command with Linux logging
os.system('rsync -arEtb --delete --stats --log-file-format="%i %o %f %n" --exclude-from=/home/coffeeboy/bin/backupexcluded.txt --backup-dir=' + '"' + incrementsdir + '" ' + sourcedir + ' ' + backupdir + ' >> ' + '/media/FreeAgent/rsync-backup.log')


#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.subtitle('END BACKUP'))
print >> backuplog, ('\n\n')
backuplog.close()
```

enter your username for all *coffeeboys* and change */media/FreeAgent* to you desired backup location.  You will need to mkdir both an backup-increments folder and a backup folder and creat a rsync-backup.log in the backup location.


**_restformat.py_**
```
#!/usr/bin/python

def title(mytitle='reStructueredText Title'):
    'Retuns mytitle formatted as a restructeredText tilte.'
    return '======================================='+'\n'+ mytitle + '\n' + '======================================='

def subtitle(mysubtitle='reStructeredText Subtitle'):
    'Returns mysubtitle formatted as a reStructeredText substring.'
    return mysubtitle + '\n' + '---------------------------------'
```

This formates the title and subtitle lines used in the log file.

The *backupexcluded.txt* file is a list of all visible and hidden files and folders (one per line) that I do not want to backup. [i.e. I do not backup up my .VirtualBox directory because of the size.

**If anyone can help I would like to get rsync to print out a list of only the files that have been updated since the last backup as well as those that have been deleted (thus are being moved to increments).  I can only seem to get the above output or a list of all files in the backup path, which is a little over kill for my log file.**

[B]
An example log file output:[/B]
=======================================
Fri Nov 13 12:23:01 2009
=======================================
Making increments directory: "/media/FreeAgent/backup-increments/Fri Nov 13 12:23:01 2009"

BEGIN BACKUP
---------------------------------

Number of files: 14088
Number of files transferred: 4
Total file size: 9327826172 bytes
Total transferred file size: 767443 bytes
Literal data: 767443 bytes
Matched data: 0 bytes
File list size: 328252
File list generation time: 0.003 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1111946
Total bytes received: 16066

sent 1111946 bytes  received 16066 bytes  150401.60 bytes/sec
total size is 9327826172  speedup is 8269.26
END BACKUP
---------------------------------


Thank you

---

### Post by coffee on 2009-11-16
I got the auto directory generation put into the backup.py code. I also adjusted the directory variable setup for ease of first time use.

```
#!/usr/bin/python

"""Python Rsync backup

This program will creat a set of directories on the chosen backup distenation media, and create
incremental backups at runtime.  Those files that have been either deleted or moved since the
last backup will be placed in an increments directory under a folder labeled with the backup run time
(Day Month Date mil-time year).  All backup logging will be stored in a log file "rsync-backup.log" on
the backup media.
"""

__author__ = "Ryan Box (coffebean@sbcglobal.net)"
__version__ = "$Revision: 0.5 $"
__date__ = "$Date: 11/16/09 17:19 $"
__license__ = "Python"

import os
from time import asctime
import restformat

#-----------------------------Variables----------------------------------------------
backupruntime = asctime()

backupmedia = "/media/FreeAgent/" #enter the mount point of your backup media

sourcedir = "/home/coffeeboy/"    #enter the source directory to backup (i.e. you home floder)

backupdir = backupmedia + "backup/" #enter the name you choose for you backup directory

incrementsdir = backupmedia + 'backup-increments/' #enter a name for the directory to hold deleted or moved files that have been backedup

#-------------------First run directory creation--------------------------------------
if not os.path.exists(backupdir):
    print 'The backup directory dose not exist. Creating now.'
    os.mkdir(backupdir)

if not os.path.exists(incrementsdir):
    print 'The increments directory dose not exist. Creating now.'
    os.mkdir(incrementsdir)

#--------------------------------------------------------------------------------------
#--------------------------------------------------------------------------------------
#Logging
backuplog = open(backupmedia'rsync-backup.log', 'a')
print >> backuplog, (restformat.title(backupruntime))
print >> backuplog, ('Making increments directory: "' + incrementsdir + '"\n')

#Make incrementsdir
os.mkdir(incrementsdir + backupruntime)

#Logging
print >> backuplog, (restformat.subtitle('BEGIN BACKUP'))
backuplog.close()

#Run rsync backup command with Linux logging
os.system('rsync -arEtb --delete --stats --log-file-format="%i %o %f %n" --exclude-from=/home/coffeeboy/bin/backupexcluded.txt --backup-dir=' + '"' + incrementsdir + '" ' + sourcedir + ' ' + backupdir + ' >> ' + '/media/FreeAgent/rsync-backup.log')


#Logging
backuplog = open(backupmedia'rsync-backup.log', 'a')
print >> backuplog, (restformat.subtitle('END BACKUP'))
print >> backuplog, ('\n\n')
backuplog.close()

```

If somebody wants to throw out some suggestions I am really teaching myself as I go.  Thats all well and good but some input would be wonderful.

---

### Post by coffee on 2009-11-17
OK I played around a for a while today and got a new version together.  I still need to write the README but it should be rather intuitive on how to get it set up for testing.  I can get this to run directly from the shell but when I set it up in 'gnome-scheduler' it fails with the following.

```

Traceback (most recent call last):
  File "/home/coffeeboy/bin/backup/src/rsync-backup.py", line 32, in <module>
    backupmedia = config['media']
  File "/usr/lib/pymodules/python2.6/configobj.py", line 580, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'media'

```

**rysnc-backup.py**
[PHP]#!/usr/bin/python

"""Python Rsync backup

This program will creat a set of directories on the chosen backup distenation media, and create
incremental backups at runtime.  Those files that have been either deleted or moved since the
last backup will be placed in an increments directory under a folder labeled with the backup run time
(Day Month Date mil-time year).  All backup logging will be stored in a log file "rsync-backup.log" on
the backup media.
"""

__author__ = "Ryan Box (coffebean@sbcglobal.net)"
__version__ = "$Revision: 0.6 $"
__date__ = "$Date: 11/17/09 17:19 $"
__license__ = "Python"

#import sys
import os
import restformat
#import config.ini
from configobj import ConfigObj
from time import asctime
#from validate import Validator



#-----------------------------Variables----------------------------------------------
config = ConfigObj('~/bin/backup/src/config.ini')

backupruntime = asctime()

backupmedia = config['media']

sourcedir = config['source']

backupdir = backupmedia + config['backupdir']

incrementsdir = backupmedia + config['incsdir']

exclude = sourcedir + config['exlist']

include = sourcedir + config['inlist']

log = backupmedia + config['logfile']

backupincdir = incrementsdir + backupruntime

#-------------------First run directory creation--------------------------------------
if not os.path.exists(backupdir):
    print 'The backup directory dose not exist. Creating now.'
    os.mkdir(backupdir)

if not os.path.exists(incrementsdir):
    print 'The increments directory dose not exist. Creating now.'
    os.mkdir(incrementsdir)

#Logging
backuplog = open(log, 'a')

print >> backuplog, (restformat.title(backupruntime))
print >> backuplog, ('Making increments directory: "'+ incrementsdir + backupruntime +'"\n')

#Make incrementsdir
backupincdir = incrementsdir + backupruntime
os.mkdir(backupincdir)

#Logging
print >> backuplog, (restformat.subtitle('BEGIN BACKUP'))
backuplog.close()

#Run rsync backup command with Linux logging 
os.system('rsync -arEtb --delete --stats --log-file-format="%i %o %f %n" --files-from='+include+' --backup-dir='+'"'+backupincdir+'" '+sourcedir+' '+backupdir+'>>'+log)

backupincdir = incrementsdir + backupruntime
if os.listdir(backupincdir) == []:
	backuplog = open(log, 'a')
	print >> backuplog, ('\n')
	print >> backuplog, ('Nothing sent to'+' ''('+incrementsdir+backupruntime+')'' '+'new increments directory.')
	print >> backuplog, ('Deleting Empty Directory.')
	print >> backuplog, ('\n')
	os.rmdir(incrementsdir + backupruntime)
else:
	backuplog = open(log, 'a')
	print >> backuplog, ('\n')
	print >> backuplog, ('Files sent to'' '+backupincdir+':')
	for top, dirs, files in os.walk(backupincdir):
		for nm in files:
			print >> backuplog, (os.path.join(top, nm))
	print >> backuplog, ('\n')

#Logging
backuplog = open(log, 'a')
print >> backuplog, (restformat.subtitle('END BACKUP'))
print >> backuplog, ('\n\n')
backuplog.close()[/PHP]

**config.ini**
[PHP]media = /media/FreeAgent/  				#The distination drive for you Backup
backupdir = backup/  					#The directory to backup into	
incsdir = backup-increments/  				#The directory to place files deleted or moved since last backup
source = /home/coffeeboy/  				#The source directory to be backedup
logfile = rsync-backup.log				#Name of the log file
exlist = bin/backup/conf/backupexluded.txt 		#The location of the excluded list
inlist = bin/backup/conf/backupincluded.txt		#The location of the included list
[/PHP]
What am I missing here? If it runs from the shell should it not run from cron?

I will upload my code later, for some reason the upload keeps failing write now.
Thanks

---

### Post by coffee on 2009-11-20
Ok I have attached a tar.gz file with my most recent code.  It seems to be turning out nicely. 

I would still like some input on this.

Thanks

---

### Post by coffee on 2009-11-22
I have moved this discussion [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8366431#post8366431")

---

