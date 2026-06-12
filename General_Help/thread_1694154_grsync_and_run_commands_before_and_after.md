---
title: "grsync and run commands before and after"
date: 2011-02-24
forum: General Help
---

### Post by visual1ce on 2011-02-24
I'm using grsync to backup to an external usb hdd and scheduling with gnome-scheduler. This works fine but id like to use the feature "run command before" and halt if command fails to determine if the drive is connected to my laptop.

If possible I'd like to use the feature to run commands after to somehow notify me (perhaps on the panel) or some other suitable manner that the backup has failed, passes on errormsg from grsync (if any) and when the last successful backup was made.

Would it be better to write a shell script and pass that to the scheduler? I guess I could do something like:

#check if folder for backup is available
if [ -d /media/mybackupdrive ]
    grsync -e "mybackupprofile"

    if [ $? != 0 ]
        #do something to notify me here
    fi
fi

i was going to use mail but i don't want a mailer daemon running all the time. i read about a way to send system messages to evolution but that comes to nothing if I can't send mail in the first place.

if grsync throws some kind of an error where do i find it? do i have to look for it in a log?

---

