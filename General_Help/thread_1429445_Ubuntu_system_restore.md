---
title: "Ubuntu system restore"
date: 2010-03-14
forum: General Help
---

### Post by Gatorade on 2010-03-14
does Ubuntu have an equivalent to system restore like windows?

I just want to know what the best way is to save everything , as in settings and programs etc. , just in case there's some sort of major failure.

any ghosting programs that will allow me to save the last known good configuration? or clone the entire drive?

thankfully I haven't needed to do it yet. Since I've been using Ubuntu I haven't run into any major screwups like with windows , but there are some times I've installed it and it took a while to get different things working. I don't want to have to go through the whole process again if there's ever a major malfunction.

---

### Post by spiky001 on 2010-03-14
This question has just been asked in beginners
[http://ubuntuforums.org/showthread.php?t=1425747](http://ubuntuforums.org/showthread.php?t=1425747)

if you search the forums they will help with a lot of questions

---

### Post by Barriehie on 2010-03-14
I use rsync on my $HOME and /etc folders.  $HOME is on another drive/partition and after rsync copies them to yet another partition I then use tar to back them up as .tgz files to a USB drive.  This happens 3 times a week while I'm asleep and leaves a logfile on the Desktop.  Now, after 2 years, 8) it's seamless...

---

### Post by Gatorade on 2010-03-14
Barriehie, I think I may try out the rsync.

thanks guys.

---

### Post by Barriehie on 2010-03-14
> **Gatorade said:**
> Barriehie, I think I may try out the rsync.

thanks guys.

Took me a year to trip over it!  Can provide scripts and crontab entries if you like.  Might have to edit just a little bit since I'm sure your machine doesn't image mine.

Barrie

Edit: Have just rewritten the script with variables so you've only got to edit 3 lines regarding the location of what to backup and where!  I've learned to make code portable in this forum; just a matter of doing it... 8)

---

### Post by Gatorade on 2010-03-29
hey, thanks.

I didn't actually get to try it out and now I'm using Mint.

is this available for Mint? I tried typing in the name in the software manager but nothing came up.

---

### Post by Barriehie on 2010-03-29
> **Gatorade said:**
> hey, thanks.

I didn't actually get to try it out and now I'm using Mint.

is this available for Mint? I tried typing in the name in the software manager but nothing came up.

I don't know about mint, except the little round red and white ones...  I just googled and found something about grsync.  What is the package manager in mint?

---

### Post by Gatorade on 2010-03-29
Linux Mint , its based on Ubuntu. [http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

I typed in rsync in synaptic and it was there. when I marked it , however, it said mark for reinstallation, . I can't find it though when I look for it in the program list.

I guess I'll just try to reinstall it.  I found another backup program called lucky backup which I'm going to try also.

---

### Post by Barriehie on 2010-03-29
> **Gatorade said:**
> Linux Mint , its based on Ubuntu. [http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

I typed in rsync in synaptic and it was there. when I marked it , however, it said mark for reinstallation, . I can't find it though when I look for it in the program list.

I guess I'll just try to reinstall it.  I found another backup program called lucky backup which I'm going to try also.

I bet you have to be root to use it.  Any backup program you're going to install is pretty much going to use a command that already exists on the machine.  Here's what I backup with.
```

#!/bin/bash
#
# BASH script to backup /home/barrie and /etc and get a list
# of installed files.  Files generated are saved on a seperate drive
# and also on a USB drive.  Script is run as root.
#


#
# Variable Setup
#
MYHOMEDIR=/home/barrie
BACKUPPLACE=/media/backup/backup-files
USBTHING=/media/disk
MYEMAIL=barrie@localhost
mountpoint -q $USBTHING
ISUSB=$?


#  Remove ~/.electricsheep/*.xxx files
#  Comment out if not using electricsheep screensaver.
#
find $MYHOMEDIR/.electricsheep -name *.xxx -exec rm {} \;


#
#  Remove Thunar sessions
#
rm $MYHOMEDIR/.cache/sessions/Thunar*


#
#  Nuke the Nautilus sessions
#  Leave 1 session files
#
# Specify the target directory and file names to operate on.
target_files=$MYHOMEDIR/.nautilus/saved-session-*


# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi


#
#  Nuke the Metacity sessions
#  Leave 1 session
#
# Specify the target directory and file names to operate on.
target_files=$MYHOMEDIR/.metacity/sessions/*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi


#
# Keep 1 weeks worth, 3, of each backup file
#
# Specify the target directory and file names to operate on.
target_files1=$BACKUPPLACE/barrie-*
target_files2=$MYHOMEDIR/etc-*

# Calculate the total number of files matching the target criteria. 
total_files1=$(ls -t1 $target_files1 | wc --lines)
total_files2=$(ls -t1 $target_files2 | wc --lines)

# Specify the number of files to retain.
retained_files=3

# If there are surplus files, delete them.
# barrie-*
if [ $total_files1 -gt $retained_files ]
  then
  rm $(ls -t1 $target_files1 | tail --lines=$((total_files1-retained_files)))
fi
# etc-*
if [ $total_files2 -gt $retained_files ]
  then
  rm $(ls -t1 $target_files2 | tail --lines=$((total_files2-retained_files)))
fi


#
# Remove all the 'normal' thumbnails
#
rm $MYHOMEDIR/.thumbnails/normal/*



#
#  Do the Backup
#
# Get the installed packages.
rm $USBTHING/packages-*
dpkg --get-selections | gawk '{ print $1 }' > $USBTHING/packages-$(date +%m%d%y)
cp $USBTHING/packages-$(date +%m%d%y) $BACKUPPLACE/

# Backup /home/barrie
rm -rf $USBTHING/barrie-*
rsync -avr $MYHOMEDIR/ $USBTHING/barrie-$(date +%m%d%y)
rsync -avr $MYHOMEDIR/ $BACKUPPLACE/barrie-$(date +%m%d%y)

# Backup /etc
rm -rf $USBTHING/etc-*
rsync -avr /etc/ $USBTHING/etc-$(date +%m%d%y)
rsync -avr /etc/ $BACKUPPLACE/etc-$(date +%m%d%y)


#
# Send me an email
#
echo ""|\mutt -s "Backup Completed $(date +%m%d%y)" $MYEMAIL

exit 0

```

---

### Post by Gatorade on 2010-03-29
:o , I have no clue what all that means , went right over my head.:)

I'll have to find another way of doing it.

---

### Post by Barriehie on 2010-03-29
> **Gatorade said:**
> :o , I have no clue what all that means , went right over my head.:)

I'll have to find another way of doing it.

Sorry! It's a BASH thing.  I never could find a backup package that did what I wanted so I've got my own. (no GUI though)

---

### Post by Gatorade on 2010-03-29
what's BASH ?

maybe one day I'll get around to learning the coding aspect, I'm still just finding my way around the linux OS.

---

### Post by Barriehie on 2010-03-29
> **Gatorade said:**
> what's BASH ?

maybe one day I'll get around to learning the coding aspect, I'm still just finding my way around the linux OS.

BASH - Bourne Again Shell; that black screen with the white letters that happens in the terminal!  Shoot, I've been running this box for a hair over 2 years and am still a 'noob' when it comes to what it can do!  After BASH I tripped over gawk, a stream editor.  Between those two and squid I've got a gnarly site blocking routine. [http://ubuntuforums.org/showthread.php?t=1338742&highlight=squid](http://ubuntuforums.org/showthread.php?t=1338742&highlight=squid)  Now I'm delving into using VIM for my editor.  No end of things to do on here!  8)

Keep posting on what you decide to do for a backup routine, it may help others!

---

