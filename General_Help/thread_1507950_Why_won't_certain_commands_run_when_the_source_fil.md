---
title: "Why won't certain commands run when the source file is launched from crontab"
date: 2010-06-12
forum: General Help
---

### Post by malleeblue on 2010-06-12
Can someone please explain why the all the commands in the following shell script work fine if I run it from terminal but not all commands run or work if I run it as a crontab?

This is what I run
```
/home/myname/Cron/rsync-backup-all > /home/myname/Cron/LogFiles/rsync-backup-all-`date +\%F`.log 2>&1 && /home/myname/Cron/rsync-backups-completed
```

The **rsync-backup-all** file is this
```
#!/bin/sh
# Script to backup various stuff
#
notify-send -i /usr/share/icons/gnome/32x32/actions/document-save.png "Backup process has begun"
rsync -r -t -v --progress -u -b -i --exclude=*~ /media/Drive1/Users/MyName/Pictures/ /media/BackupDrive/.Backups/Drive1/Users/MyName/Pictures/
echo ==============================================
echo backup of Drive1/Pictures to Backup Drive COMPLETED @ `date +%T," "%F`
echo ==============================================
notify-send -i /usr/share/icons/gnome/32x32/actions/document-save.png "backup of Drive1/Pictures to BackupDrive has completed"
echo 
echo
``` 


and the **rsync-backups-completed** file is this
```
#!/bin/bash
zenity --text-info DISPLAY=0 --title="BACKUPS FOR `date +\%F` COMPLETE" --filename=/home/myname/Cron/LogFiles/rsync-backup-all-`date +\%F`.log --width 500 --height 400
```

Just to clarify, the backup works without a problem, it's just the *notify-sends* and the *zenity* which aren't working if run from crontab. All commands work fine if the "This is what I run" piece of code above is started from a Terminal window.

Thanks, and if you need to know I'm using Ubuntu Lucid but was having the same problems in Karmic.

---

### Post by dcstar on 2010-06-12
> **malleeblue said:**
> Can someone please explain why the all the commands in the following shell script work fine if I run it from terminal but not all commands run or work if I run it as a crontab?
.........
Just to clarify, the backup works without a problem, it's just the *notify-sends* and the *zenity* which aren't working if run from crontab. All commands work fine if the "This is what I run" piece of code above is started from a Terminal window.

Thanks, and if you need to know I'm using Ubuntu Lucid but was having the same problems in Karmic.

Because a terminal in a logged in session is not the same as a cron environment.

Do a search for the hundreds of other identical questions already in the forum and their solutions.

---

### Post by malleeblue on 2010-06-12
> **dcstar said:**
> Because a terminal in a logged in session is not the same as a cron environment.

What does that even mean?  Please explain.

> Do a search for the hundreds of other identical questions already in the forum and their solutions.
It's comments like that that lead to various bloggers to write things like "*We provide horrendous support for newcomers and are sometimes [downright rude]("http://www.omgubuntu.co.uk/2010/06/omg-exclusive-ubuntu-lucid-lynx-video.html").*" -- [source [http://www.omgubuntu.co.uk/2010/06/many-hands-make-light-work-few-make-it.html]](http://www.omgubuntu.co.uk/2010/06/many-hands-make-light-work-few-make-it.html])

If there are "hundreds of other[s]" then why not at least help a guy out and post a few links.

---

### Post by chenxiaolong on 2010-06-12
malleeblue: It's the GUI based programs that don't run correctly in the cron environment. This is because cron does not run under the current X session and therefore, cannot start GUI programs in that X session by default. Basically, what you can run in a TTY (Ctrl + Alt + F#) is what cron can run by default.

There is a fix for this though.

First, you have to add this to your "**~/.bashrc**" file:

```
xhost local:{your user without brackets} > /dev/null
```

This allows applications to connect to your X session to run GUI programs. Then you have to tell your commands to use your X seesion, so that it doesn't create this error:

```
[I]No protocol specified
/your/program: Unable to open display, exiting.[/I]
```

There are two methods to tell your program to use your X session (method 2 works better):

**_METHOD 1_**

In your zenity command, you used:

```
zenity --text-info **DISPLAY=0** --title="BACKUPS FOR `date +\%F` COMPLETE" --filename=/home/myname/Cron/LogFiles/rsync-backup-all-`date +\%F`.log --width 500 --height 400
```

Zenity uses a different argument for setting the display. Instead, you should use:

```
zenity --text-info **--display=:0.0** --title="BACKUPS FOR `date +\%F` COMPLETE" --filename=/home/myname/Cron/LogFiles/rsync-backup-all-`date +\%F`.log --width 500 --height 400
```

**_METHOD 2_**

In your crontab file, you can tell crontab to run this command first:

```
export DISPLAY=:0.0
```

so that you won't have to set the display for any GUI programs. In this case, you won't need the "**--display=:0.0**" part for zenity.

Hopefully this information was useful :D.

---

### Post by malleeblue on 2010-06-12
> **chenxiaolong said:**
> Hopefully this information was useful :D.

My friend, you've been incredibly helpful. That's the sort of assistance us newbies are looking for and need. Exemplary indeed. Thank you most sincerely.

---

### Post by chenxiaolong on 2010-06-12
You're very welcome! Let us know if the your cron event works or not :D.

---

### Post by malleeblue on 2010-06-12
> **chenxiaolong said:**
> You're very welcome! Let us know if the your cron event works or not :D.

I added to my "**~/.bashrc**" file as instructed and also took your advice in method 2 and added "export DISPLAY=:0.0" to the beginning of my cron command and it has worked perfectly. Again, a BIG thanks.

For any other newbies who might use this thread to solve a similar problem, to make it work I also added " && " (that's space ampersand ampersand space) before the rest of my cron command. It might be easier if I show you ...

```
# m h  dom mon dow   command
00 22   * * *  export DISPLAY=:0.0 && /home/myname/Cron/rsync-backup-all > /home/myname/Cron/LogFiles/rsync-backup-all-`date +\%F`.log 2>&1 && /home/myname/Cron/rsync-backups-completed
```

I'm so glad there are helpful people like **chenxiaolong** in the forums.

Beans don't make someone a 'star', but caring and detailed support does.

---

