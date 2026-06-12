---
title: "apt-get upgrade script that reboots only when necessary?"
date: 2010-11-01
forum: General Help
---

### Post by trikster_x on 2010-11-01
So I am trying to write a script to add to crontab that I can use to auto update my system a couple times a week.  I've done that much before, but I want to make the script a bit smarter about rebooting.  Before I had it reboot after running the "apt-get upgrade" command, regardless of whether it needed to or not.  Easy peesy stuff, just a sequential command using "&&".

What I would like to know at this point is how I can have the script look to see if the reboot is even necessary.  I am assuming there is something I can tell the script to look for in an if statement, but I'm not sure what or where.  Can anyone point me in the right direction for this?

---

### Post by trikster_x on 2010-11-02
Anyone?

---

### Post by trikster_x on 2010-11-02
Okay, so I found some info about a file being created:
```
/var/run/reboot
```

Or something to that effect.  If anyone reads this and is about to go through a kernel update, could you verify that this file actually gets created after the update.  I know for sure that it ends up in the /var/run directory, and it will be named "reboot", "need-reboot", or something along those lines.  The file will not exist before the update or after the reboot.  

I did my kernel update on a new install before I found this info, so I can't verify it myself until the next update that requires a reboot.

---

### Post by Barriehie on 2010-11-03
> **trikster_x said:**
> Okay, so I found some info about a file being created:
```
/var/run/reboot
```

Or something to that effect.  If anyone reads this and is about to go through a kernel update, could you verify that this file actually gets created after the update.  I know for sure that it ends up in the /var/run directory, and it will be named "reboot", "need-reboot", or something along those lines.  The file will not exist before the update or after the reboot.  

I did my kernel update on a new install before I found this info, so I can't verify it myself until the next update that requires a reboot.

I can't verify it but:
```

find /var/run/ -name *boot -exec shutdown -r now {} \;
```
in /etc/crontab should reboot the machine; without much warning if the file exists.

or:
```

find /var/run/ -name *boot -exec touch /home/username/Desktop/ReBootMe {} \;
``` will let you know.

Probably work best to run it from a script and then you can check for a lock file in the event you don't want a reboot at crontabs convenience.

---

### Post by trikster_x on 2010-11-03
Thanks for the suggestion.  Unfortunately there is a file in that directory with "boot" in the name (not the one I am looking for unfortunately), so the wild card method won't work for me this time.

I actually have a script that is basically ready to go. I just need to get the name of the file, if it even exists.

---

### Post by dcstar on 2010-11-03
Why reboot at all?:

[http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html](http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html)

---

### Post by dcstar on 2010-11-03
> **trikster_x said:**
> 
.........
I actually have a script that is basically ready to go. I just need to get the name of the file, if it even exists.

[http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd](http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd)

---

### Post by trikster_x on 2010-11-03
Thanks for both those posts.  The link in the latter post had exactly what I was looking for.  And I'll look into ksplice uptrack, too.  Thanks again :D

EDIT:

Okay, so I got my script up and running:
```
#! /bin/bash
date
zenity --question --text="apt-get will attempt to update your system in 30 seconds." --ok-label="Begin Update" --cancel-label="Cancel Update" --timeout=30
if [ "$?" -eq "1" ]
   then echo "Update Cancelled"
   else sudo apt-get update && sudo apt-get -y upgrade
fi

if [ -a /var/run/reboot-required ]
   then zenity --question --text="The system will reboot in 30 seconds" --ok-label="Reboot" --cancel-label="Cancel" --timeout=30
      if [ "$?" -eq "1" ]
         then echo "" && echo "Skipped reboot" && echo ""
            
         else echo "" && echo "Reboot" && echo"" && sudo shutdown -r +0
            
      fi
   else echo "" && echo "No reboot was necessary." && echo ""
fi

```
I added a GUI that enables the user to choose to override the script within 30 seconds after each window opens.  I included some lines for using crontab to send the standout to a log to keep track of whether the script is cancelled or allowed to run and whether a reboot was necessary.

---

