---
title: "A Challenge: Back up system on external drive"
date: 2010-03-04
forum: General Help
---

### Post by kid1000002000 on 2010-03-04
Got a challenge for somebody.

I have been using lucky backup to backup my files.  However, I am unable to get a list of all packages that are currently installed, turn it into a file, and then back that file up as well with this gui.Lucky-backup's execute function does not work.

I would like to have my system backup all appropriate directories upon connection of an external usb drive.  I would also like to run a variation of the following command: 

sudo dpkg --get-selections > /path to external drive/Linux Backup/app-list.log
(I need to overwrite the file on every connect- not add to it!  What needs to change to this?)

1.  What commands would I need to use to backup certain directories?
2.  How can I turn the above mentioned command to OVERWRITE the current file on the drive, and not simply add to it?
3.  Most importantly, how do I run these commands both immediately upon mounting of the drive, AND/OR "on command" without having to type it all out every time?

Thanks!

---

### Post by kid1000002000 on 2010-03-06
bump

---

### Post by flippo on 2010-03-06
The command you typed SHOULD overwrite the file (> means overwrite >> means append) make sure your using > and not >>.

I've never used a "backup system." I've always just set up a network cron rsync job... So I'm unsure exactly what tools you've got going for you for question 1.

I'm unsure of how to do this without polling the system (which is not ideal)  If you want to poll, you can just run a script with this pseudo-code:

```
while (true)
  if (device mounted && mounted)
    mounted=true
    dpkg --get-selections...
  else if (NOT device mounted)
    mounted = false
  endif
  sleep for some time
endwhile
```

EDIT:
Note, this would not be immediate, it would just check and update every so often (so if it loops once every 5 mins, if the device is plugged in for 5 mins it will run within that time...)

---

### Post by kid1000002000 on 2010-03-06
Thanks.  I agree, polling is not something I would want to do- but now that I see that script, I can follow it.
I have been using this backup program in the past but am now trying to learn rsync to make the change.  And you are right- the above listed command does overwrite the file.  So questions 1 and 2 are answered! I found the following post for 3 as well:

[http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

Solved.

---

