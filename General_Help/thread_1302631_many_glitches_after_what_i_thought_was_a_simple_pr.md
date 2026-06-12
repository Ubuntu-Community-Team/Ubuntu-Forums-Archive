---
title: "many glitches after what i thought was a simple problem"
date: 2009-10-27
forum: General Help
---

### Post by DarkLiberty on 2009-10-27
I am a recent convert to the way of ubuntu and stumble frequently. I am sorry if this is too n00bish for anyone. I appreciate the help!

I recently had managed to mess with the permissions of of my /home/ directory, somehow, prompting a message stating something or other that i forgot. so i restarted and logged in in recovery mode and altered the permissions of one of the files in question andmy /home/directory, as per recomended by an earlier post:

the commands were
sudo chmod 644 .dmrc
sudo chmod 755 /home/
i think.

anywho, while the error message has since gone and left, i am still left with glitches here and there: my "Places" somehow has not managed to save the shortcuts i put in the bar ["Music", "Videos", "Pictures", and "Documents"] and if i put them back in they disapear after maybe four seconds. firefox has not managed  to remember any of my bookmarks, but does remember its history and up until ten minutes ago, i could not log into email; the "login" button would not work. firefox will not allow me to press a "back" or "forward" button. also, wesnoth had trouble auto-saving and could not manual save. 

help...?

---

### Post by mcduck on 2009-10-27
> **DarkLiberty said:**
> I am a recent convert to the way of ubuntu and stumble frequently. I am sorry if this is too n00bish for anyone. I appreciate the help!

I recently had managed to mess with the permissions of of my /home/ directory, somehow, prompting a message stating something or other that i forgot. so i restarted and logged in in recovery mode and altered the permissions of one of the files in question andmy /home/directory, as per recomended by an earlier post:

the commands were
sudo chmod 644 .dmrc
sudo chmod 755 /home/
i think.

anywho, while the error message has since gone and left, i am still left with glitches here and there: my "Places" somehow has not managed to save the shortcuts i put in the bar ["Music", "Videos", "Pictures", and "Documents"] and if i put them back in they disapear after maybe four seconds. firefox has not managed  to remember any of my bookmarks, but does remember its history and up until ten minutes ago, i could not log into email; the "login" button would not work. firefox will not allow me to press a "back" or "forward" button. also, wesnoth had trouble auto-saving and could not manual save. 

help...?

Chek the ownership of all the hidden files & directories inside your home.

You probably managed to get them changed to root at the same time when the permissions got changed.

(And, by the way, if you are the owner of the files, you don't need "sudo" to change their permissions. Not that you'd need "sudo" in the recovery mode anyway, since it logs you in as root..)

---

### Post by Giblet5 on 2009-10-27
This will *probably* fix everything. Copy/paste each line into a terminal window, one at a time:
```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;

## These two might give an error but that's OK
sudo chmod 700 $HOME/.ssh
sudo chmod 600 $HOME/.ssh/*
```


Please verify that this fixes the problems (all of them) and then mark this thread (SOLVED)

---

### Post by DarkLiberty on 2009-10-28
> **Giblet5 said:**
> This will *probably* fix everything. Copy/paste each line into a terminal window, one at a time:
```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;

## These two might give an error but that's OK
sudo chmod 700 $HOME/.ssh
sudo chmod 600 $HOME/.ssh/*
```
Please verify that this fixes the problems (all of them) and then mark this thread (SOLVED)


while this removed many major issues [the bookmarks under Places, my ability to set a location, etc] it still left me with several smaller errors [cannot save bookmarks in firefox, none of my games can save, and basically issues with saving]...

i might just format the drive and start again from the next distro. i dont have too much important stuff on here that isn't backed up already. i DO want to know where i went wrong and how to fix it...

---

### Post by fluffman86 on 2009-10-28
As far as where you went wrong, you almost certainly changed permisions or ownership on files somehow.  But I would also recommend upgrading to Karmic. It's very nice! and faster too! and the only way to get full speed is with a full format to get ext4. 

So, it's not all bad. :)

---

