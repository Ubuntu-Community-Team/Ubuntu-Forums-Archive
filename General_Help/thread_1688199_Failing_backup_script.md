---
title: "Failing backup script"
date: 2011-02-15
forum: General Help
---

### Post by niels_linux_forum on 2011-02-15
Hey everybody,

I'm writing a script to automaticaly backup a directory with the tar command. I searched the forum but their wasn't any topic solving or discussing my problem.

Now I tried several different approaches to use relative paths but I can't get it working. I always get the following error : tar: Removing leading `/' from member names

I tried the tar -cjfP $TAR_FILE $DATA, or tar -cjfP $TAR_FILE -C / $DATA and my last approach is creating a textfile with each file name to add to the tar file, like this :

```

# --- BEGIN ---
DATA="/CVS_Repository/ErikStevensBackUp"
DATA_LIST="/Backups/backup_list.txt"
TAR_FILE="/Backups/ErikStevensBackup-`date +"%d-%m-%Y"`.tar.bz2"


# first remove old backup
rm -f /Backups/ErikStevensBackup*.*.*

# Create dataList
find $DATA -depth -print > $DATA_LIST

# create backup with date
tar -cjfTP $TARFILE  $DATA_LIST

# Remove old data list file
rm -f $DATA_LIST
 
# --- END ---

```

Anybody has a answers for my problem ? I'm using Ubuntu 10.04 Server edtion.

Thanks a lot in advance.

Regards,

Niels

---

### Post by DaithiF on 2011-02-15
Hi, a couple of points:

1. the 'f' parameter to tar needs to be followed immediately by the tar file you are creating.  when you do -cjfP somefile.tar data tar interprets this as 'create a tar file P and add to it somefile.tar and data.  So change the order of your tar parameters so that f is the last one, or separate them into 2 blocks, e.g.:
```
tar -cjPf somefile.tar data
```
or
```
tar -f somefile.tar -cjP data
```

2. theres no need to create a list of files and pass those to tar since tar will add the contents of a directory recursively anyway.  
so:
```
tar -cjf somefile.tar directory 

```should be sufficient.

---

### Post by niels_linux_forum on 2011-02-15
Thanks for the fast reply.

I solved it like this now :

```

#--- BEGIN ---
DATA="/Users/niels/Desktop/groep03"
TAR_FILE="/Users/niels/Backup/Test2-`date +"%d-%m-%Y"`.tar.bz2"

# Remove old tar file
rm -f "/Users/niels/Backup/Test-*.*.*"

#Create tar file
tar -f $TAR_FILE  -cjP "$DATA"

#---  END  ---

```

But now when I unzip the tar I get the whole structure from my filesystem like mentioned in the DATA Url.
But I don't want that, I want to get just groep03 when I unzip it, any advise ?

---

### Post by DaithiF on 2011-02-15
change to the parent directory first, either using tar's -C option, or by using the cd command before tar.
something like:

```
root_dir="/Users/niels/Desktop"
target="groep03"
tar_file="/Users/niels/Backup/Test2-`date +"%d-%m-%Y"`.tar.bz2"

# Remove old tar file
rm -f "/Users/niels/Backup/Test-*.*.*"

#Create tar file
tar -C "$root_dir" -f $TAR_FILE  -cjP "$target"

```

---

