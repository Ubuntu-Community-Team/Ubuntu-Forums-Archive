---
title: "How to run command before shutdown"
date: 2010-11-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-11-14
i need to run this command right before shutdown
```
/home/$USER/.tmpfs.sh
```it will copy my ram disk to my hard disk
my ram disk has my firefox profile on it

---

### Post by pqwoerituytrueiwoq on 2010-11-15
anyone?

---

### Post by C0derBear on 2010-11-15
I can't offer the specifics of doing it per-user, but you could wire something up in the shutdown scripts ( /etc/init.d/ ... ) to get it done.

Just be sure to read up on how that scripting works before you start fiddling with it. The upshot though is that you'd have one script run to load the ram drive during boot and a separate one to unload it during shutdown.

---

### Post by yaami on 2010-11-15
I usually put the commands that need to be executed before shutting down in .bash_logout and then edit the the /etc/gdm/PostSession/Default by adding the ```
$HOME/.bash_logout 
``` before exit 0. 

I hope this helps.

---

### Post by pqwoerituytrueiwoq on 2010-11-15
> **yaami said:**
> I usually put the commands that need to be executed before shutting down in .bash_logout and then edit the the /etc/gdm/PostSession/Default by adding the ```
$HOME/.bash_logout 
``` before exit 0. 

I hope this helps.
it does not appear to be working
did i do it right?
```
me@linux-laptop:~$ cat .bash_logout
# ~/.bash_logout: executed by bash(1) when login shell exits.
sh .tmpfs.sh
# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
me@linux-laptop:~$ cat /etc/gdm/PostSession/Default
#!/bin/sh
$HOME/.bash_logout
exit 0
me@linux-laptop:~$ 

```

---

### Post by pqwoerituytrueiwoq on 2010-11-15
bump

---

### Post by matt_symes on 2010-11-15
Hi

Instead of $HOME/.bash_logout

try 

/home/<your username>/.bash_logout

Ensure your script is executable using chmod

and read this

[http://wwww.ubuntuforums.org/showthread.php?p=9515598](http://wwww.ubuntuforums.org/showthread.php?p=9515598)

Kind regards

---

### Post by pqwoerituytrueiwoq on 2010-11-15
> **matt_symes said:**
> Hi

Instead of $HOME/.bash_logout

try 

/home/<your username>/.bash_logout

Ensure your script is executable using chmod

and read this

[http://wwww.ubuntuforums.org/showthread.php?p=9515598](http://wwww.ubuntuforums.org/showthread.php?p=9515598)

Kind regards
seems it will only run if i logout
will this result in permission errors?
```
chad@linux-laptop:~$ cat /etc/gdm/PostSession/Default
#!/bin/sh
rsync -av --delete --exclude .unpacked /home/chad/.mozilla/firefox/t2jwdsde.default/ /home/chad/.mozilla/firefox/profile/
exit 0
chad@linux-laptop:~$ 

```

---

### Post by matt_symes on 2010-11-15
Hi

Shutdown. Sorry my mistake i speed read the posts. Not very clever.

For shutdown use you'll want to use /etc/init.d and use symbolic links.

This is an old post but the principle is still the same. It can explain it quicker than i can type.

[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)

or you could use update.rc at add the links for you.

EDIT: Now you have both options :)

I think you should be fine with the permissions

Kind Regards

---

### Post by pqwoerituytrueiwoq on 2010-11-15
> **matt_symes said:**
> Hi

Shutdown. Sorry my mistake i speed read the posts. Not very clever.

For shutdown use you'll want to use /etc/init.d and use symbolic links.

This is an old post but the principle is still the same. It can explain it quicker than i can type.

[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)

or you could use update.rc at add the links for you.

EDIT: Now you have both options :)

I think you should be fine with the permissions

Kind Regards
so i made a symlink to /etc/gdm/PostSession/Default
```
chad@linux-laptop:~$ cat /etc/init.d/Default
#!/bin/sh
rsync -av --delete --exclude .unpacked /home/chad/.mozilla/firefox/t2jwdsde.default/ /home/chad/.mozilla/firefox/profile/
exit 0
chad@linux-laptop:~$
```
and shutdown
i had placed a junk file in t2jwdsde.default for testing it was not in my profile folder after i rebooted (used shutdown via a applet)
i do have an encrypted home folder if that effects anything

---

### Post by C0derBear on 2010-11-15
> **pqwoerituytrueiwoq said:**
> i do have an encrypted home folder if that effects anything

I've not used encrypted folders yet so take this as theory ... BUT I'd guess that this will limit you to doing your ramfs maintenance in logon/logoff scripts because the folder won't be accessible during system startup and shutdown.

---

### Post by pqwoerituytrueiwoq on 2010-11-15
what script is run as soon as i click shutdown
if i add a line of code at the top of it it should run in time

---

### Post by matt_symes on 2010-11-15
Hi

Sorry for my late reply. I had to pop out.

Let me explain the post for you now i have more time.
[FONT=monospace]
The original file was called [/FONT]rensa.sh and was stored on the desktop
[FONT=monospace]
It was made executable using

[/FONT]chmod +x rensa.sh

It was moved into /etc/init.d using
[FONT=monospace]
[/FONT]sudo cp rensa.sh /etc/init.d
[FONT=monospace]
A symbolic link was created in /etc/rc0.d to the _users scripts name_ in /etc/init.d with K10 pre-pended to it using

[/FONT]sudo ln -s /etc/init.d/rensa.sh /etc/rc0.d/K10rensa.sh

rc0.d contains files to be run at run level 0. The K10 was prepended as K stands for Kill. I.e run at shutdown not startup and 10 is the priority. Lower priority links get run first

Hopefully that makes it a bit clearer.

And i should thank the original poster. This is only clarification of what he wrote.

Kind regards

---

### Post by pqwoerituytrueiwoq on 2010-11-15
thanks that worked

sum up for people who do not care and just want the answer
you can use gedit/kedit if you do not like nano
```
nano Desktop/rensa.sh
# fill out script content
chmod +x Desktop/rensa.sh
sudo cp Desktop/rensa.sh /etc/init.d/
sudo ln -s /etc/init.d/rensa.sh /etc/rc0.d/K10rensa.sh
rm Desktop/rensa.sh

```My rensa.sh
```

#!/bin/sh
rsync -av --delete --exclude .unpacked /home/chad/.mozilla/firefox/t2jwdsde.default/ /home/chad/.mozilla/firefox/profile/
exit 0
```

---

### Post by sssent on 2010-11-18
If you want to persist your ramdisk before restart, you should make a link in /etc/rc6.d as well.

(The system enters runlevel 6 instead of 0 on restart.)

---

