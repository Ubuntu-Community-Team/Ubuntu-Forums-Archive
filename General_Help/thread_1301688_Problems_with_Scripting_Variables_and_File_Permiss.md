---
title: "Problems with Scripting Variables and File Permissions"
date: 2009-10-26
forum: General Help
---

### Post by slowmo on 2009-10-26
I'm trying to introduce variables into an already existing script because it is necessary to duplicate the script a number of times and it is easier to do this using variables. 

The original script, which alters permissions and then backups using rsync, used the absolute paths. The script below is my attempt to introduce variables into it. 

# Variables
# Source Directory (what directory to perform command on)
SOURCE_DIR=/home/mydirectory/
# Destination Directory (where to backup files to)
DEST_DIR=/my/backup/destination/
# Rsync Log File Location
RSYNC_LOG=/my/rsync/log/location/file.txt

find $SOURCE_DIR -type f | grep -v $SOURCE_DIR\.ssh/ | while read var1; do chmod 660 "$var1"; done
find $SOURCE_DIR -type d | while read var1; do chmod 770 "$var1"; done
find $SOURCE_DIRbin -type f | while read var1; do chmod 770 "$var1"; done

#Rsync script to backup contents of Source Directory to Backup Destination
rsync -avz --delete $SOURCE_DIR $DEST_DIR > $RSYNC_LOG

The problem that I am encountering is that when I run the script from a link in /home/mydirectory/bin/ it strips the execute permissions of the contents of /home/mydirectory/bin/ but if I run the script directly from within /home/mydirectory/bin/ it seems to work fine. 

I'm pretty sure the important line is: 

find $SOURCE_DIRbin -type f | while read var1; do chmod 770 "$var1"; done

and what I am essentially trying to do is to create a line where I can use the SOURCE_DIR variable and add /bin onto the end of it. The way I have written it seems the most logical way to me because the / already exists at the end of the SOURCE_DIR variable. I have tried: 

find $SOURCE_DIR/bin -type f | while read var1; do chmod 770 "$var1"; done

But this did not seem to have the desired effect either. I'm pretty sure that I am missing something that is probably quite straight forward but I can't find the answer anywhere and I'm not having much luck making sense of guides to syntax etc. 

Any help would be appreciated. Thanks very much.

---

### Post by vidak on 2009-10-26
If you write $SOURCE_DIRbin it will look for a variable named SOURCE_DIRbin, which doesn't exist. You should write "$SOURCE_DIR"bin instead, this should work. 
It might be a good idea to add a line like:
```
echo $SOURCE_DIR "$SOURCE_DIR"bin
```
to the script to see what the variable contains...

---

