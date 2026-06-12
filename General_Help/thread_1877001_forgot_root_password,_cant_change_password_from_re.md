---
title: "forgot root password, cant change password from recovery."
date: 2011-11-07
forum: General Help
---

### Post by itai970 on 2011-11-07
hey!
it seems i cant login to my root (says authentication failiure) and when going into recovery more (also called "single user") and i log into root, and do 'passwd', i type the new password and it says "authentication token manipulation error"

i tryed to chmod the 'shadow' file and give 'all' permissions to read and write but it says its a read-only file system.


idea's?

EDIT: also, what are those 0's below my user name?
          and is there a way to chmod all .exe files to have x (i think its x..) permissions for all?
          and how do i know what 'group' im apart of?

---

### Post by Lars Noodén on 2011-11-07
Is the partition mounted read-write or read-only?

---

### Post by itai970 on 2011-11-07
i dont know.. 
actually, im not even sure what partrition that is..
i remember making 3 partitions, 1 SWAP, 1 of my old files (back from windows) and 1 for linux..
i think its on the linux one, and its just a partitions.. how do i know if its r-w or just read only?

---

### Post by Lars Noodén on 2011-11-07
When you get the error, try typing [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html) and look at the output.  You'll see something like "on / type ext4" near the beginning of one of the lines.  Then at the end of the line it will say if it is mounted read only or read write.

---

### Post by itai970 on 2011-11-07
it read only.. 
what now?

---

### Post by Lars Noodén on 2011-11-07
Just to be sure, when you enter the Recovery Mode and there is a Recovery Menu, one of the items is fsck.  Do that first.

Then you'll need to mount it read-write before you can reset the password.
Another item on the Recovery Menu is "Remount / read/write", try that before going to the root shell prompt.

---

### Post by itai970 on 2011-11-07
to be sure:
first do fsck
then "remount read\write"
then go to root and do "passwd"?

EDIT: THANKS! i did fsck and then went to root terminal and did 'passwd', changed successfuly.
but, i still have the other questions, if you can please help:
"and is there a way to chmod all .exe files to have x (i think its x..) permissions for all?"

-i need it for wine, to run installs and games without changing permissions every damn time.

oh, and is there a quick tut about 'cd'?
i know how to basically use it, but i dont know how to move from disk to disk etc..

---

### Post by Lars Noodén on 2011-11-07
> **itai970 said:**
> to be sure:
first do fsck
then "remount read\write"
then go to root and do "passwd"?

EDIT: THANKS! i did fsck and then went to root terminal and did 'passwd', changed successfuly.
but, i still have the other questions, if you can please help:
"and is there a way to chmod all .exe files to have x (i think its x..) permissions for all?"

-i need it for wine, to run installs and games without changing permissions every damn time.

Yes.

---

### Post by itai970 on 2011-11-07
umm.. well, that's very.. useful... 
can i at least get some keywords to search google?

---

### Post by Lars Noodén on 2011-11-07
> **itai970 said:**
> 
EDIT: THANKS! i did fsck and then went to root terminal and did 'passwd', changed successfuly.
but, i still have the other questions, if you can please help:
"and is there a way to chmod all .exe files to have x (i think its x..) permissions for all?"

-i need it for wine, to run installs and games without changing permissions every damn time.

oh, and is there a quick tut about 'cd'?
i know how to basically use it, but i dont know how to move from disk to disk etc..

Sorry, I did not see the edit.

```

find /path/to/directory -name '*.exe' -exec chmod +x {} \;

```

'cd' is part of [bash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html)

There's not much to cd:

cd by itself will bring you to your home dircetory
pwd will show what directory you are in
cd .. will move you back up a directory
cd - will move you the directory you most recently left
cd /path will move you to directory /path

---

### Post by itai970 on 2011-11-07
yeah i already got over the cd..

im trying to change permissions for a exe (SAMP.exe) because when i try to run it with wine it says its "not executableBit"
so i did some reading and if i got it right, i need to add permission 'x' to the exe file to make it executable.
i went into the dir of the file, and did 
'chmod a+x SAMP.exe'
i also tried
'chmod g+x SAMP.exe'

the terminal says nothing, (not even an error) and the permissions dont change either (i checked with ls -l)
also, if i right clock the file itself, going to properties and then permissions tab, and mark with V the "allow executing file a program" it just un-mark's it...

help?

---

### Post by itai970 on 2011-11-07
> **Lars Noodén said:**
> Sorry, I did not see the edit.

```

find /path/to/directory -name '*.exe' -exec chmod +x {} \;

```'cd' is part of [bash]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html")

There's not much to cd:

cd by itself will bring you to your home dircetory
pwd will show what directory you are in
cd .. will move you back up a directory
cd - will move you the directory you most recently left
cd /path will move you to directory /path

****, i wrote a long reply and now i dont see it..

any way
____________________
i try to chmod an exe file, the permission is not added to it.
i tryed:
chmod a+x SAMP.exe
chmod g+x SAMP.exe

both didnt work, terminal didnt even really respond, not even an error.. nothing, just another like with the dir and then the '#' (means im root)
_________________
also, when im right clocking the .exe file, going into properties and then the Permissions tab there is a small box i can mark V in, its "allow executing file as program"
when i mark it, its getting unmark'ed like nothing happened.

damn, i only wanted to install a game..
also, is there a way to install a game with WINE if the game is loaded in an .ISO file?


EDIT: oh now i see it, it moved to second page..
im so stupid -_-

---

### Post by cmcanulty on 2011-11-07
type ```
gksudo nautilus
``` in terminal then it will open graphical interface file system in superuser mode, browse to file or folder then rt click the item you want to change on permissions tab make sure you tell it to include enclosed files. Exit terminal and it should stay changed

---

### Post by itai970 on 2011-11-07
> **cmcanulty said:**
> type ```
gksudo nautilus
``` in terminal then it will open graphical interface file system in superuser mode, browse to file or folder then rt click the item you want to change on permissions tab make sure you tell it to include enclosed files. Exit terminal and it should stay changed

all i got is a bunch of errors..

---

### Post by cmcanulty on 2011-11-07
Please post the errors by copying and pasting the terminal output into a reply. Use the code tags to surround the output. You select the stuff and then click the # on the reply toolbar.

---

### Post by Gatemaze on 2011-11-07
Just a side question, i may have missed an episode or two. Do you you have a normal sudoer user? Can't you just do:
sudo passwd root
to change the password of root?

---

### Post by itai970 on 2011-11-07
```
root@itai970-desktop:/home/itai970# gksudo nautilus

(gksudo:4316): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4316): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4316): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4316): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksudo:4316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksudo:4316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksudo:4316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksudo:4316): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Could not register the application: The connection is closed

```

and as i said, we are past the root pass, its SOLVED
there are other questions, read top comment in top of page 2.

---

### Post by cmcanulty on 2011-11-08
Mine comes in one page can you give the post # also I would start gksudo nautilus from the terminal prompt then wait a few seconds for it to open then navigate to your location from there. Hint close any directories before running gksudo nautilus so you don't get mixed up on which is the root graphical interface.

---

### Post by itai970 on 2011-11-08
> **cmcanulty said:**
> Mine comes in one page can you give the post # also I would start gksudo nautilus from the terminal prompt then wait a few seconds for it to open then navigate to your location from there. Hint close any directories before running gksudo nautilus so you don't get mixed up on which is the root graphical interface.
 
i didnt understand "mine comes in one page can you give the post #"
also, i opened another thread.. my computer crashed and wont work properly now, related to compiz..
no point in solving this thread if computer isnt working LOL!

---

### Post by cmcanulty on 2011-11-08
Try the live CD and also try the recovery mode at boot. With the live CD you can at least access and copy your home files and save a lot of work. Keep posting it is raining here and I have time to help out.

---

### Post by itai970 on 2011-11-09
> **cmcanulty said:**
> Try the live CD and also try the recovery mode at boot. With the live CD you can at least access and copy your home files and save a lot of work. Keep posting it is raining here and I have time to help out.
 
i wish it was raining here too -_-
i dont have a liveCD, i used a LiveUSB and i already deleted that.
 
what should i do in recovery?

---

