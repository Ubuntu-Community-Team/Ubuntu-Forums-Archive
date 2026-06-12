---
title: "ncftp upload / date script help"
date: 2011-12-10
forum: General Help
---

### Post by Moif_Murphy on 2011-12-10
Hi there.

I'm looking for a script that can scan a number of subdirectories residing on my VPS and find mp3s created in the last 30 days and then upload them to a single remote FTP directory.

I'm using ncftp which is an amazing command line ftp client.

I've found this:

```
#!/bin/bash
# Shell script to copy all files recursively and upload them to
# remote FTP server (copy local all directories/tree to remote ftp server)
#
# If you want to use this script in cron then make sure you have
# file pointed by $AUTHFILE (see below) and add lines to it:
# host ftp.mycorp.com
# user myftpuser
# pass mypassword
#
# This is a free shell script under GNU GPL version 2.0 or above
# Copyright (C) 2005 nixCraft
# Feedback/comment/suggestions : http://cyberciti.biz/fb/
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit http://bash.cyberciti.biz/ for more information.
# -------------------------------------------------------------------------
 
FTP="/usr/bin/ncftpput"
CMD=""
AUTHFILE="/root/.myupload"
 
if [ -f $AUTHFILE ] ; then
  # use the file for auth
  CMD="$FTP -m -R -f $AUTHFILE $myf $remotedir $localdir"
else
  echo "*** To terminate at any point hit [ CTRL + C ] ***"
  read -p "Enter ftpserver name : " myf
  read -p "Enter ftp username : " myu
  read -s -p "Enter ftp password : " myp
  echo ""
  read -p "Enter ftp remote directory [/] : " remotedir
  read -p "Enter local directory to upload path [.] : " localdir
  [ "$remotedir" == "" ] && remotedir="/" || :
  [ "$localdir" == "" ] && localdir="." || :
  CMD="$FTP -m -R -u $myu -p $myp $myf $remotedir $localdir"
fi
 
$CMD
```

..which will copy all files recursively and upload them to remote FTP server but I need it adjusting to fit my needs.

Any help would be greatly appreciated.

---

### Post by lechien73 on 2011-12-10
Hi,

I love these type of challenges :)

I would probably use the [FONT="Courier New"]find[/FONT] command with the [FONT="Courier New"]-mtime[/FONT] switch, to find files of a certain age. I've modified and tested the script as follows:

```
#!/bin/bash
# Shell script to copy all files recursively and upload them to
# remote FTP server (copy local all directories/tree to remote ftp server)
#
# If you want to use this script in cron then make sure you have
# file pointed by $AUTHFILE (see below) and add lines to it:
# host ftp.mycorp.com
# user myftpuser
# pass mypassword
#
# This is a free shell script under GNU GPL version 2.0 or above
# Copyright (C) 2005 nixCraft
# Feedback/comment/suggestions : http://cyberciti.biz/fb/
#
# Modified by Matt Rudge (http://blog.mattrudge.net)
# to allow automated upload of files of a certain age
#
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit http://bash.cyberciti.biz/ for more information.
# -------------------------------------------------------------------------
 
FTP="/usr/bin/ncftpput"
CMD=""
AUTHFILE="/root/.myupload"
 
if [ -f $AUTHFILE ] ; then
  # use the file for auth
  CMD="$FTP -m -f $AUTHFILE $myf $remotedir"
else
  echo "*** To exit at any point hit [ CTRL + C ] ***"
  read -p "Enter ftpserver name : " myf
  read -p "Enter ftp username : " myu
  read -s -p "Enter ftp password : " myp
  echo ""
  read -p "Enter ftp remote directory [/] : " remotedir
  read -p "Enter local directory to upload path [.] : " localdir
  [ "$remotedir" == "" ] && remotedir="/" || :
  [ "$localdir" == "" ] && localdir="." || :

  CMD="$FTP -m -u $myu -p $myp $myf $remotedir"

fi

read -p "Enter maximum age of the file in days [30] : " daysold
[ "$daysold" == "" ] && daysold="30" || :


find $localdir -type f -mtime -$daysold 2>/dev/null | while read FILENAME

do
 CMD="$CMD $FILENAME"
 $CMD
done
```

Hope this helps!

---

### Post by Moif_Murphy on 2011-12-12
Fantastic,
 
I'll be giving this a whirl in a little while and will report back. Thanks very much for looking at this, much appreciated!

---

### Post by lechien73 on 2011-12-12
You're welcome. Hope it works for you :)

I'm not too happy with the original script, since if you run it in AUTHFILE mode, you can never set the local or remote directories. I did want to re-write the entire script, but I managed to stop my OCD from taking over! :rolleyes:

---

### Post by sisco311 on 2011-12-12
> **lechien73 said:**
> I've modified and tested the script as follows:

Did you test it with files with special characters in their names. ;)

Check out BashFAQ 020 (link in my signature).

---

### Post by Moif_Murphy on 2011-12-12
Well,
 
I've just started to have a play and I can't get the Authfile to work. No biggy though as I can enter the details manually.
 
It does however appear to be stuck in a loop. I've chosen 7 as the number of days for it to see how recent the files are and it's uploading files just fine. However I've completed a VPS migration in the last 4 days so it's uploading files that have been modified during that time - which is most of them!
 
So, working as intended. But, if I CTRL+C to cancel the upload it seems to start from the top and reuploads the first file it finds all over again.

---

### Post by Moif_Murphy on 2011-12-12
> **sisco311 said:**
> Did you test it with files with special characters in their names. ;)
 
Check out BashFAQ 020 (link in my signature).
 
And there is this as well. No matter how many times I tell people to replace spaces with underscores, they never listen.

---

### Post by lechien73 on 2011-12-12
> **sisco311 said:**
> Did you test it with files with special characters in their names. ;)

Check out BashFAQ 020 (link in my signature).

That is a very interesting question and, when I tested it with spaces in the names, it failed.

It seems that ncftpput doesn't like spaces at all. Nor does it handle escaped spaces properly, and it doesn't work if you enclose the name in double quotes " either.

I do have it working by using sed to replace a whitespace for a ? wildcard. Replace the do loop with the following:

```
do

 OUT=$(echo $FILENAME | sed 's/ /\?/g')
 echo "Transferring $FILENAME"
 CMD="$CMD $OUT"
 $CMD
done 
```

:)

---

