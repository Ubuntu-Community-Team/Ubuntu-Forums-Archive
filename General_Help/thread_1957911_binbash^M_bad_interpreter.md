---
title: "/bin/bash^M: bad interpreter"
date: 2012-04-13
forum: General Help
---

### Post by Doulos1 on 2012-04-13
I am trying to backup a folder (using teminal) on a website with a script that works perfectly fine on other sites (all on same server). I keep getting the following error:

/bin/bash^M: bad interpreter: no such file or directory

The command I am using is **/home/me/backup-files.sh**

The script is:```
#!/bin/bash
# Paul Newman

# http://www.webjunk.com
# You are free to modify and distribute this code,
# so long as you keep my name and URL in it.

# your Server's name
SERVER=serverip/

# Enter Your Domain Name
DOMAIN=me.com

# directory to backup to
BACKDIR=/home/me/backups/
BACKDIR2=backups/

# date format that is appended to filename
DATE=`date +'%m-%d-%Y'`


#----------------------Mail Settings--------------------#


# set to 'y' if you'd like to be emailed the backup (requires mutt)
MAIL=n


# email addresses to send backups to, separated by a space
#EMAILS="EMAILUSERAME@DOMAIN.com"
SUBJECT="!!!! TAR backup on $SERVER ($DATE)"



#----------------------FTP Settings--------------------#



# set "FTP=y" if you want to enable FTP backups

FTP=n


# FTP server settings; should be self-explanatory
FTPHOST=""

FTPUSER=""
FTPPASS=""

# directory to backup to. if it doesn't exist, file will be uploaded to 
# first logged-in directory
FTPDIR=""

#-------------------Deletion Settings-------------------#



# delete old files?
DELETE=y

# how many days of backups do you want to keep?
DAYS=1

#----------------------End of Settings------------------#
# check of the backup directory exists
# if not, create it

if  [ -e $BACKDIR ]
then
echo Backups directory already exists
else
mkdir $BACKDIR
fi

echo "Backing up Files and Directories for $DOMAIN"
tar -czf "$BACKDIR2"$DOMAIN-$DATE.tar.gz ./public_html/


# if you have the mail program 'mutt' installed on
# your server, this script will have mutt attach the backup
# and send it to the email addresses in $EMAILS

if  [ $MAIL = "y" ]

then

BODY="Your backup is ready! These are Your Files & Directories!" 

ATTACH=`for file in $BACKDIR/*$DATE.tar.gz; do echo -n "-a ${file} ";  done`

    
echo "$BODY" | mutt -s "$SUBJECT" $ATTACH $EMAILS  
    
echo -e "Your backup has been emailed to you! \n"

fi

if  [ $FTP = "y" ]
then
echo "Initiating FTP connection to send backup"
cd $BACKDIR

ATTACH=`for file in $BACKDIR*$DATE.tar.gz; do echo -n -e "put $file $DOMAIN-$DATE.tar.gz\n"; done`
    
ftp -nv <<EOF
    
open $FTPHOST

user $FTPUSER $FTPPASS
cd $FTPDIR
bin
$ATTACH

quit
EOF
echo -e  "FTP transfer complete! \n"
fi

if  [ $DELETE = "y" ]
then
find $BACKDIR -name "*.tar.gz" -mtime $DAYS -exec rm {} \;
if  [ $DAYS = "1" ]
then
echo "Yesterday's backup has been deleted."
else
echo "The backup from $DAYS days ago has been deleted."
fi
fi


echo Your backup is complete!

```

Any idea why I get this error?

Thanks

---

### Post by cortman on 2012-04-13
The ^M denotes a carriage return. Apparently your script has extra redundant carriage returns. [This site]("http://fir3net.com/General-UNIX/binbashm-bad-interpreter-no-such-file-or-directory.html") has a little sed script you can run to fix it.

---

### Post by SeijiSensei on 2012-04-13
This is a common problem when files are copied from DOS/Windows to Unix.  The end-of-line is a denoted by a "carriage return" and a "line feed" character on WinDOS; only a return is used in Unix.  The line feed appears as a Ctrl-M.

There are handy utilities to convert WinDOS files available from the repositories in the package called [tofrodos]("http://www.virtualhelp.me/linux/164-dos2unix-missing-ubuntu-1004").  Or you can use sed as cortman suggested.

---

