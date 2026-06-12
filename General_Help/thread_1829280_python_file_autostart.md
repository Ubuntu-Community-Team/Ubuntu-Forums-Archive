---
title: "python file autostart"
date: 2011-08-20
forum: General Help
---

### Post by 700 on 2011-08-20
hi

i'm trying to create autostart for my python file on ubuntu 11.04 according to scripts i found on google, but none of them is working for me.

created:
- 1.py file (which is working fine) in /home/user/Desktop directory;
- .bash_login file in /home/user directory, containing script:
```

#!/bin/bash
python /home/user/Desktop/1.py
```
- both files at least: -rwxr-xr-x

why autostart is not working?

---

### Post by tom4everitt on 2011-08-20
First, are you sure that your Python program will do something that you will notice?

My suspicion otherwise is that .bash_login is not executed at all during login. Perhaps try adding another command like
```

echo $( date ) >> logins

```
If .bash_login is executed at login, every login should put the exact date and time in the file "logins" in your home directory. 


You could also try adding your Python script to System->Settings->Startup Programs and see if that works (it's a bit unsatisfying to do stuff graphically, I know, but it will at least tell you if it works).

---

### Post by 700 on 2011-08-20
my python program is using GUI and it is working OK.

is it possible that my problem is somehow connected with a message:
"Do you want to run "1.py", or display its contents? [run in terminal / display / cancel / run]" (i can't start my .py program directly by doubleclicking)?

---

### Post by tom4everitt on 2011-08-21
> **700 said:**
> 
is it possible that my problem is somehow connected with a message:
"Do you want to run "1.py", or display its contents? [run in terminal / display / cancel / run]" (i can't start my .py program directly by doubleclicking)?

I don't think so. Double clicking on a file is ambiguous - do you want to view it or run it? Therefore Gnome have to ask you. Running "python 1.py" from a terminal is not ambiguous, it means "run the program" and nothing else. So I don't think that's related. 

Did you try my other suggestions?

---

### Post by 700 on 2011-08-21
System->Preferences->Startup Applications
i tried this solution as well - problem still persists.

my bash_login file looks like
```
#!/bin/bash
echo $(date) >> logins
python /home/user/Desktop/1.py
```
but no logins file appeared after reboot.

---

### Post by SavageWolf on 2011-08-21
Try CTRL+ALT+F1 and login there. (To get back here, use CTRL+ALT+F8 or F7)

---

### Post by tom4everitt on 2011-08-22
> **700 said:**
> System->Preferences->Startup Applications
i tried this solution as well - problem still persists.

my bash_login file looks like
```
#!/bin/bash
echo $(date) >> logins
python /home/user/Desktop/1.py
```
but no logins file appeared after reboot.


That you don't get entries in the logins file indicates that your .bash_login isn't executed, so in that sense it is not surprising that your python script isn't executed either. The million dollar question is of course why it isn't executed... 

It is also strange that System->Preferences->Startup Applications doesn't do the trick either.


The only thing I can think of is to create a new user to rule out the possibility of the problem being user specific - if nothing else. If you do that, add the commands to .profile instead, that seems to be the default place to add commands in Ubuntu (but .profile is not executed if a .bash_login exists). For me it works perfectly adding echo $(date) >> logins to .profile (on Lucid).

---

### Post by 700 on 2011-08-22
why the type of my .bash_login file is:
shell script (application/x-shellscript)
while the type of my .bash_logout file is:
plain text document (text/plain)?

could this be the reason or some hint how to fix autostart?

---

### Post by tom4everitt on 2011-08-23
> **700 said:**
> why the type of my .bash_login file is:
shell script (application/x-shellscript)
while the type of my .bash_logout file is:
plain text document (text/plain)?

could this be the reason or some hint how to fix autostart?

I think it's because your login file starts with:

#!/bin/bash

but your logout doesn't.


Also I'd presume logout is not executable. The reason it doesn't have to be
is that it is executed as

. ./bash_logout

(notice the dot). The login is executed the same way, so it doesn't have to be
executable either, nor have that first line.

Don't know if it's the cause of your problems - it's not impossible.

---

### Post by 700 on 2011-08-24
omg, one more hint...
my 1.py file (-rwxr-xr-x) stopped working - i can't run it, it's not executing any more. after clicking "run" under "do you want to run..." question - nothing appears. i didn't change my script.
what is going on?

---

### Post by tom4everitt on 2011-08-24
Launch it from Terminal - then you might get some useful error message. I know the feeling though :)

---

### Post by lykwydchykyn on 2011-08-24
I've never heard of .bash_login, but I'm about 90% certain that bash configs are NOT run during a graphical login.  Also, I'm not sure if .bash_login gets executed if .bash_profile exists.

Bash configs should be run when you launch a terminal.  If your program is graphical, I wouldn't recommend launching it from a bash config file anyway.

You normally want to use whatever autostart method is built into your desktop environment to launch things at startup.

*If* it's being launched and spitting out errors, those will normally end up in ~/.xsession-errors

---

### Post by tom4everitt on 2011-08-24
> **lykwydchykyn said:**
> I've never heard of .bash_login, but I'm about 90% certain that bash configs are NOT run during a graphical login.  Also, I'm not sure if .bash_login gets executed if .bash_profile exists.

Bash configs should be run when you launch a terminal.  If your program is graphical, I wouldn't recommend launching it from a bash config file anyway.

You normally want to use whatever autostart method is built into your desktop environment to launch things at startup.

*If* it's being launched and spitting out errors, those will normally end up in ~/.xsession-errors

You make a lot of sense :)

---

### Post by 700 on 2011-08-24
```
(nautilus:1934): GLib-GPbject_CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```
nautilus -c
gives thousands of above lines and also:
```
(evolution-alarm-notify:1940): evolution-alarm-notify-WARNING **: alarm.c:253: Requested removal of nonexistent alarm!
```
nautilus /
gives also:
```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/trans is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```
i've got one more machine with fresh ubuntu, but it's not problem fixing then - it'll be only file replanting. i hope there is some normal solution somewhere.

---

### Post by lykwydchykyn on 2011-08-24
When did nautilus come into this??

---

### Post by 700 on 2011-08-25
this is the first time i'm checking .xsession-errors - so nautilus come to this at least yesterday.

---

### Post by lykwydchykyn on 2011-08-25
> **700 said:**
> this is the first time i'm checking .xsession-errors - so nautilus come to this at least yesterday.

Ok.

Most programs spit out a lot of pointless warnings when they're run, so .xsession-errors can be a busy mess.  I wouldn't get hung up on those nautilus errors.

We need to focus on your actual python script.  Are there any errors in there relating to python?

---

### Post by Topsiho on 2011-08-25
The first line is for bash, but you want to start a python program/script.

The line should read

#!/usr/bin/env python

The python script should be made executable first using chmod +x <file_name>

Topsiho

---

### Post by 700 on 2011-08-25
my python script was working fine for months. there are no changes in this script so far, but when i tried to autostart this file, using System->Preferences->Startup Applications or .bash_login file, i didn't get autostart and my file stopped working. now i can't open this file using double click->Run button and double click->Display button (but i can change it using GVim). this file is now -rwxrwxrwx, but inaccessible.

---

### Post by lykwydchykyn on 2011-08-25
Have you tried running it from a terminal window and observing the output?

---

### Post by 700 on 2011-08-25
my python file is based on GUI
```
bash: ./1.py: /usr/bin: bad interpreter: Permission denied
```

---

### Post by lykwydchykyn on 2011-08-25
> **700 said:**
> my python file is based on GUI

Yes, but launching it from a terminal gives you the stderr output, which even GUI programs produce.
> 
```
bash: ./1.py: /usr/bin: bad interpreter: Permission denied
```

The file has a bad #! line.  There's a space after /usr/bin obviously.  It should read:
```

#!/usr/bin/python

```
Though technically if you're executing it as "python 1.py" you don't need that first line.

---

### Post by 700 on 2011-08-25
ok. my python file is working back :)
but this is not the end - autostart is still not catching it with any method i know. i just want to see my python file straight away after logging in.

---

### Post by lykwydchykyn on 2011-08-25
Try this approach:

 - Go to ~/.config/autostart
 - create a new file called "1.desktop"
 - open that file in an editor, and put this in it:
```


[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=1.py
Comment=My python script
Exec=/usr/bin/python /path/to/1.py
StartupNotify=false
Terminal=false

```

 - save the file.  make sure you replaced "/path/to/1.py" with the *Full path* of your python script.


See if that does the trick.  If it doesn't, it probably has to do with something the script does.  Does your script read environment variables by any chance?

---

### Post by 700 on 2011-08-25
yes. my 1.py file is taking data from 1.txt (-rwxrwxrwx) file from the same place, so my file is probably taking some environment variables.

---

### Post by 700 on 2011-08-26
problem was in my python file. thanks so much to everyone who helped me! :)

---

### Post by tom4everitt on 2011-08-26
> **700 said:**
> problem was in my python file. thanks so much to everyone who helped me! :)

Hehehe, I love it :D Happens to me all the time - you try all kinds of fancy solutions until realizing you missed something really simple.. You usually end up learning something along the way though, so it's no big loss really ;)

---

