---
title: "copy only files that have changed?"
date: 2011-12-14
forum: General Help
---

### Post by garyed on 2011-12-14
Is there a way to copy only files that have changed since the last backup?
I know the -u switch will update existing files but that is not what I want to do. I'm working on a web site & I have about 20 or 30 different files that I constantly back up into a new folder that is named by the date & time. I use a shell script that makes it easy to do but I can't figure out how to only backup the files I've worked on since the last backup. I may only work on one or two of the files at a time but since they get backed up into an empty directory the -u switch still copies all the files. In DOS xcopy there is a switch that will do this but I can't find anything in Linux that will. I find it hard to believe that MSDOS has got  something better from the command line than Linux. Surely I must be missing something, right?

---

### Post by papibe on 2011-12-14
That is basically what rsync do best. For example, the first time you run this:
```
rsync -av source/ destination/
```
It will copy everything (mirror) from source to destination. But the 2nd time:
```
rsync -av source/ destination/
```
It will only copy the files that have changed.

Does that help? There are a lot of more options. Tell us if you need more help customizing it.

Regards.

EDIT: some of the options include a way to access a backup that you already have done, so you can compare the source with the backup and only copy the changed files into a different directory.

---

### Post by garyed on 2011-12-14
> **papibe said:**
> That is basically what rsy```

```nc do best. For example, the first time you run this:
```
rsync -av source/ destination/
```
It will copy everything (mirror) from source to destination. But the 2nd time:
```
rsync -av source/ destination/
```
It will only copy the files that have changed.

Does that help? There are a lot of more options. Tell us if you need more help customizing it.
.................

Thanks for the ideas,
I always thought I needed to use the "-u" switch with rsync to copy only files that have changed but it does work like you said. I don't see anywhere in the man pages where it explains why it works like that with the "-a" switch but it does. Anyways that really doesn't do the job I need because each backup goes to an empty directory. So if I use ```
rsync -av 
``` or 
```
rsync -auv 
``` it still copies every file each time to the new directory since there are no existing files for it to compare. What I'm trying to do is to have an archive of all my stuff so I can go back to any point in time & resurrect things the way they were in case I find some mistakes later on. Maybe if I post part of the script it will explain what I'm trying to do better:

```

#! /bin/bash
clear
echo""
echo "This will back up the load html & php files to ~/load  in a directory named by time & date"
echo ""
read -n1 -r -p  "Press \" Y\" to continue with backup or any other key to exit" name
clear
x='y'
y='Y'
if test $x = "$name" ||test $y = "$name"
then

title=$(date +%Y-%m-%d-%T);

echo ""
mkdir ~/loadcalc/load_$title
cp /var/www/my_web/load/* ~/load/load_$title
............

```

---

### Post by Lars Noodén on 2011-12-14
The [font=Courier New]-a[/font] is the same as [font=Courier New]-rlptgoD[/font].  It will copy only the files that changed.

---

### Post by garyed on 2011-12-14
> **Lars Noodén said:**
> The [font=Courier New]-a[/font] is the same as [font=Courier New]-rlptgoD[/font].  It will copy only the files that changed.
I understand that but what I don't understand is which of those switches tells it to copy only files that have changed. I've checked every one of those switches & I don't see any one of them that will do that. Is there something undocumented or can someone explain it to me?

---

### Post by papibe on 2011-12-14
Here's something for you.

These are a couple of scripts that I use to backup data. The first one creates a full backup. The second makes a differential backup, on a different directory. I modified them with what I think are your own directories. Replace 'your_user' with your actual username.

**full.sh:**
```
#!/bin/bash
SOURCE="/var/www/my_web/load/"
BACKUP="/home/your_user/load/"

DATE=$(date +%Y-%m-%d-%T)

DESTINATION="$BACKUP"/"$DATE"-full/

# the symbolic link 'latest-full' will always point to the lastest full backup.
rm -rf "$BACKUP"/latest-full
ln -s "$DESTINATION" "$BACKUP"/latest-full

rsync -av "$SOURCE" "$DESTINATION"
```

**differential.sh:**
```
#!/bin/bash
SOURCE="/var/www/my_web/load/"
BACKUP="/home/your_user/load/"
LBACKUP="/home/your_user/load/latest-full/"

DATE=$(date +%Y-%m-%d-%T)

DESTINATION="$BACKUP"/"$DATE"-diff/

rsync -av --compare-dest="$LBACKUP" "$SOURCE" "$DESTINATION"

# delete empty directories (rsync copies the whole tree).
cd "$DESTINATION"
find . -depth -type d -empty -delete
```
I hope they provide some ideas to you.
Kind Regards.

---

### Post by mbuell on 2011-12-14
Another option is <gasp> pay-for software. There is an excellent program that I have used for years to keep directories in sync - it is all gui, and they wrote a linux version! I pay for a license every few years as the versions grow - it is called "Beyond Compare". The folks that wrote it did a bang-up job. Yes, you can use CLI to do the same thing - but I get tired of having to think about what I need my computer to do. Beyond Compare gives me a nice gui in either OS, I can see what I am doing, I can see what needs to be done. No muss, no fuss.

---

### Post by garyed on 2011-12-14
> **papibe said:**
> Here's something for you.

These are a couple of scripts that I use to backup data. The first one creates a full backup. The second makes a differential backup, on a different directory. I modified them with what I think are your own directories. Replace 'your_user' with your actual username.

**full.sh:**
```
#!/bin/bash
SOURCE="/var/www/my_web/load/"
BACKUP="/home/your_user/load/"

DATE=$(date +%Y-%m-%d-%T)

DESTINATION="$BACKUP"/"$DATE"-full/

# the symbolic link 'latest-full' will always point to the lastest full backup.
rm -rf "$BACKUP"/latest-full
ln -s "$DESTINATION" "$BACKUP"/latest-full

rsync -av "$SOURCE" "$DESTINATION"
```

**differential.sh:**
```
#!/bin/bash
SOURCE="/var/www/my_web/load/"
BACKUP="/home/your_user/load/"
LBACKUP="/home/your_user/load/latest-full/"

DATE=$(date +%Y-%m-%d-%T)

DESTINATION="$BACKUP"/"$DATE"-diff/

rsync -av --compare-dest="$LBACKUP" "$SOURCE" "$DESTINATION"

# delete empty directories (rsync copies the whole tree).
cd "$DESTINATION"
find . -depth -type d -empty -delete
```
I hope they provide some ideas to you.
Kind Regards.

Very interesting,
I'm not sure what the "compare-dest=" does. The man pages are not very descriptive.

---

### Post by garyed on 2011-12-14
I guess if I go back to my original question what I need to know is if there is any command that can mark a file so any change to the file afterwards will show a different mark. MSDOS does it by using an archive bit on the file that can be removed & any change to the file will put the archive bit back on the file. It works great for incremental backups.

---

### Post by papibe on 2011-12-14
> **garyed said:**
> Very interesting,
I'm not sure what the "compare-dest=" does. The man pages are not very descriptive.
This is how it works:

It all start by making a full backup (or mirror) of your source directory. If you do a regular rsync again, you would update the destination, but the previous version of the backup-ed data would be overwritten.

Another approach is to do a differential backup: leave the full backup intact, and create a new directory with only the content that has change on the source.

A typical rsync implementation has this structure:
```
rsync -av --compare-dest=full_back_up  original_source/   new_differential_backup/
```
rsync will follow this logic: (1) go to original_source and take the first file; (2) check if the file exist in the full_backup; (3) if exist and haven't change, stop and fetch the next file from original_source; (4) if it does not exist or has changed, then copy it into new_differential_backup.

Does that clarify things a little bit?
Regards.

---

### Post by Lars Noodén on 2011-12-15
> **garyed said:**
> I understand that but what I don't understand is which of those switches tells it to copy only files that have changed. I've checked every one of those switches & I don't see any one of them that will do that. Is there something undocumented or can someone explain it to me?

I think that is inherent in [font=Courier New]rsync[/font] itself.  Those are the settings I've been using for years and it does copy only the files that have changed.  However, I do know that using [font=Courier New]rsync[/font] by itself without any switches does nothing.

---

### Post by garyed on 2011-12-15
> **papibe said:**
> This is how it works:

It all start by making a full backup (or mirror) of your source directory. If you do a regular rsync again, you would update the destination, but the previous version of the backup-ed data would be overwritten.

Another approach is to do a differential backup: leave the full backup intact, and create a new directory with only the content that has change on the source.

A typical rsync implementation has this structure:
```
rsync -av --compare-dest=full_back_up  original_source/   new_differential_backup/
```
rsync will follow this logic: (1) go to original_source and take the first file; (2) check if the file exist in the full_backup; (3) if exist and haven't change, stop and fetch the next file from original_source; (4) if it does not exist or has changed, then copy it into new_differential_backup.

Does that clarify things a little bit?
Regards.

I think I understand now. 
That should actually do what I'm wanting to do then.
I want to do incremental backups to a new directory each time so after one full backup I could use that backup directory for the "--compare-dest=" directory to find what has changed & the copy only the changed files to a new directory.

---

### Post by garyed on 2011-12-15
> **Lars Noodén said:**
> I think that is inherent in [font=Courier New]rsync[/font] itself.  Those are the settings I've been using for years and it does copy only the files that have changed.  However, I do know that using [font=Courier New]rsync[/font] by itself without any switches does nothing.

That makes sense to me now. I always used the -u switch but its really not needed unless you want to make sure you don't overwrite any newer files that are already on the destination folder.

---

