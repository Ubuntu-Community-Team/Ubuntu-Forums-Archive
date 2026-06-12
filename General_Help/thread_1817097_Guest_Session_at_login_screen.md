---
title: "Guest Session at login screen"
date: 2011-08-02
forum: General Help
---

### Post by triunenature on 2011-08-02
I know there have been a few posts about how to do this, none from this year (and none that work effectively), so I thought i'd ask.

Basically, the problem is, we have a bunch of computers in a computer lab, that we want to students to access, but not modify in ANY way.  That includes backgrounds or whatnot.  And after restart, any changes they may have made, change back.

Also, they can't have read access to the administrator account on the computer.
This needs to give a permission denied, or something:

```

cd /home/(admin account username)
ls

```

The Guest Session is EXACTLY what we are looking for, but try as i might, i can't get it to work.  Because, we don't want to have to login as administrators, then activate guest session, just for our students to use the computers.  The idea being, we can leave the computers in there, and not worry about the students breaking anything.

One tread i tried was:

[http://ubuntuforums.org/showthread.php?t=1601911](http://ubuntuforums.org/showthread.php?t=1601911)

However, using his meathod, will log the student into the account, and after about 5 seconds, log them back out.

The other method listed lower in the thread,

```
/usr/bin/guest-session
```

Seems to work, but upon logging out, fails to launch the gdm

Only way to restore is restarting the computer.

Any help is appreached

---

### Post by fdrake on 2011-08-02
> **triunenature said:**
> I know there have been a few posts about how to do this, none from this year (and none that work effectively), so I thought i'd ask.

Basically, the problem is, we have a bunch of computers in a computer lab, that we want to students to access, but not modify in ANY way.  That includes backgrounds or whatnot.  And after restart, any changes they may have made, change back.

Also, they can't have read access to the administrator account on the computer.
This needs to give a permission denied, or something:

```

cd /home/(admin account username)
ls

```

The Guest Session is EXACTLY what we are looking for, but try as i might, i can't get it to work.  Because, we don't want to have to login as administrators, then activate guest session, just for our students to use the computers.  The idea being, we can leave the computers in there, and not worry about the students breaking anything.

One tread i tried was:

[http://ubuntuforums.org/showthread.php?t=1601911](http://ubuntuforums.org/showthread.php?t=1601911)

However, using his meathod, will log the student into the account, and after about 5 seconds, log them back out.

The other method listed lower in the thread,

```
/usr/bin/guest-session
```

Seems to work, but upon logging out, fails to launch the gdm

Only way to restore is restarting the computer.

Any help is appreached

i never tried edubuntu but i think what you need is to apply a USID sticky bit to the session program so that it will start (or the students can start) it even if the user doesn't have the privilege as a superuser.

[check how to USID]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/SUID_HOWTO")

---

### Post by pqwoerituytrueiwoq on 2011-08-02
try changing the user id of guest to something over 1000
sudo usermod -u 1003 guest
that may work or screw up the guest account try it on a live cd first

---

### Post by triunenature on 2011-08-03
> **pqwoerituytrueiwoq said:**
> try changing the user id of guest to something over 1000
sudo usermod -u 1003 guest
that may work or screw up the guest account try it on a live cd first

It doesn't come with a traditional guest account.

sudo usermod -u 1003 guest, returns an error of "no user named guest" (or something like that)

And the fake user account i created, called student, has a user id of greater than 1000

---

### Post by triunenature on 2011-08-03
> **fdrake said:**
> i never tried edubuntu but i think what you need is to apply a USID sticky bit to the session program so that it will start (or the students can start) it even if the user doesn't have the privilege as a superuser.

[check how to USID]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/SUID_HOWTO")

Interesting read, however the student account is fully able to launch the guest-session.  The problem is when the guest session ends.

After complete reformat of computer (to make sure it wasn't due to weird software issues)

2 cases:

the script like:

```

#!/bin/bash
# Launches the guest session
/usr/bin/guest-session
# Logs the user when done
/usr/bin/gnome-session-save --logout

```

After you attempt to logout, the screen goes black, and it says "checking battery state...   [ok]"
then nothing... you can type, but no commands work.
(note this is a desktop computer)

second case:

```

/usr/bin/guest-session

```

After you logout, you are presented with the user, Student logged in, and a password request.  If you submit the password, you are dumped into the student account (not the guest account, like a normal login)

---

### Post by bodhi.zazen on 2011-08-03
Did you try the gdm-guest-session package ?

You then change permission of home directories / files to 770 or 660

If all else fails, take a look at Fedora with the xguest package.

---

### Post by triunenature on 2011-08-03
> **bodhi.zazen said:**
> Did you try the gdm-guest-session package ?

You then change permission of home directories / files to 770 or 660

If all else fails, take a look at Fedora with the xguest package.

gdm-guest-session is already the newest version.

But there is no guest user...  The new guest system, uses a guest session, so the user guest is created and destroyed, by login and logout.

Currently, I have changed the student password to one only teachers will know.  And have a sign which says to restart the computer after use.  The "student" account auto logs in after 15 seconds (and obviously doesn't require password to login).  So the current situation is acceptable.

While using another os is possible, its not realistic.  The teacher computers use edbuntu (and all the student usable computers use edbuntu), and the server runs ubuntu server ed.  Frankly introducing another operating system would be far more work than any good.

Thanks for the suggestion though.

I am going to keep this post as unsolved, until either i, or someone figures out how to logout, and then be able to log back in, and have a guest session.  Or of course, ubuntu could re-add the guest login feature, like they used to have (and then i will mark this thread as solved)

So, any other suggestions are happly accepted

---

### Post by bodhi.zazen on 2011-08-03
You may also wish to google search "kiosk" and "ubuntu"

I am not sure why you are trying to lock down the student accounts using a guest session, I would simply give each student a unique account and use private home directories.

You can lock down some of the settings.

---

### Post by fdrake on 2011-08-03
I installed gdm-guest-session and edited the source to autorestart at the end.
```

$sudo cp /usr/share/gdm/guest-session/guest-session-cleanup.sh /usr/share/gdm/guest-session/guest-session-cleanup.sh.bk

$sudo su
#cat cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
>/usr/share/gdm/guest-session/guest-session-launch

```

apply auto start to the Student user.
----------------------------------------------------
once you login into the student user the guess session will start. once you are done and logout you will be prompted to login into the  student login. DON'T LOGIN, but just wait like 10-15sec for the program to clean the old session and the guest session will restart automatically. So the students won't even need to login or to know the password.

The cons is that if you swich user from the guess-session to another user, you won't be able to switch back to the guest session, unless you login in student account, logoff (to kill the program) and login again (to start a new session).

---

### Post by pqwoerituytrueiwoq on 2011-08-03
what i did on my desktop was make a user named anonymous/Guest and made there folder in my /tmp folder and i recreate it at every boot
here is part of my /etc/gdm/Init/Default
```
mkdir /tmp/guestUser
rsync -av /etc/skel/ /tmp/guestUser/
ln -s /usr/share/pixmaps/faces/penguin.jpg /tmp/guestUser/.face
chown -hR anonymous:anonymous /tmp/guestUser
```i put this right before the exit 0 line
under users and groups i set the home directory to /tmp/guestUser
i chmoded my account so the guest cant access my files 

anonymous is the login name 
Guest is the name that appears at login

i also did some modifications to the default account settings as you can see from my tree output
```
/etc/skel/
|-- .bash_logout
|-- .bashrc
|-- .config
|   `-- autostart
|       |-- bluetooth-applet.desktop
|       |-- evolution-alarm-notify.desktop
|       |-- gnome-at-session.desktop
|       |-- gnome-user-share.desktop
|       |-- jockey-gtk.desktop
|       |-- ubuntuone-launch.desktop
|       |-- update-notifier.desktop
|       `-- user-dirs-update-gtk.desktop
|-- examples.desktop
|-- .gconf
|   |-- apps
|   |   |-- applets
|   |   |   |-- clock_screen0
|   |   |   |   |-- %gconf.xml
|   |   |   |   `-- prefs
|   |   |   |       `-- %gconf.xml
|   |   |   `-- %gconf.xml
|   |   |-- %gconf.xml
|   |   |-- gnome_settings_daemon
|   |   |   |-- %gconf.xml
|   |   |   `-- plugins
|   |   |       |-- %gconf.xml
|   |   |       `-- housekeeping
|   |   |           `-- %gconf.xml
|   |   |-- metacity
|   |   |   |-- %gconf.xml
|   |   |   `-- general
|   |   |       `-- %gconf.xml
|   |   `-- panel
|   |       |-- applets
|   |       |   |-- clock_screen0
|   |       |   |   |-- %gconf.xml
|   |       |   |   `-- prefs
|   |       |   |       `-- %gconf.xml
|   |       |   `-- %gconf.xml
|   |       `-- %gconf.xml
|   `-- desktop
|       |-- %gconf.xml
|       `-- gnome
|           |-- %gconf.xml
|           |-- interface
|           |   `-- %gconf.xml
|           `-- peripherals
|               |-- %gconf.xml
|               `-- mouse
|                   `-- %gconf.xml
|-- .gnome2
|   `-- keyrings
|       |-- default
|       `-- default.keyring
`-- .profile

23 directories, 32 files
```

my /tmp folder is ram disk and / is a ssd which makes the guest account really fast
/var is on a old hdd though

---

### Post by triunenature on 2011-08-03
> **fdrake said:**
> I installed gdm-guest-session and edited the source to autorestart at the end.
```

$sudo cp /usr/share/gdm/guest-session/guest-session-cleanup.sh /usr/share/gdm/guest-session/guest-session-cleanup.sh.bk

$sudo su
#cat cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
>/usr/share/gdm/guest-session/guest-session-launch

```

apply auto start to the Student user.
----------------------------------------------------
once you login into the student user the guess session will start. once you are done and logout you will be prompted to login into the  student login. DON'T LOGIN, but just wait like 10-15sec for the program to clean the old session and the guest session will restart automatically. So the students won't even need to login or to know the password.

The cons is that if you swich user from the guess-session to another user, you won't be able to switch back to the guest session, unless you login in student account, logoff (to kill the program) and login again (to start a new session).


I hate to ask this, but could you walk me through this, step by step.

This makes sense:
```
sudo cp /usr/share/gdm/guest-session/guest-session-cleanup.sh /usr/share/gdm/guest-session/guest-session-cleanup.sh.bk

```

but the:
```

$sudo su
#cat cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
>/usr/share/gdm/guest-session/guest-session-launch

```

doesn't make sense, and where would i add this script to, and what script am i adding?

Considering where these computers will end up being, I highly doubt that any other user will need to login.  And if/when an IT or admin does, we will just restart the computer before and after our usage.

---

### Post by fdrake on 2011-08-03
```

$sudo su
#cat cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
>/usr/share/gdm/guest-session/guest-session-launch

```

these are scripts that the guess-session program uses.
to view the file of guess session 
```
ls /usr/share/gdm/guest-session/
```

```
less /usr/share/gdm/guest-session/guest-session-launch
```  
is the program that starts the guess session login (start up)


```
less /usr/share/gdm/guest-session/guest-session-cleanup.sh
```
when you log out from a session the guess-session program calls this script to clean up the tmp files and to delete the guess user. So what I did is to add a start up process before the cleanup end. Basically it's a loop. once you login in the student account the guess session will always restart at the end of the session.

to add the start up line at the end of this file you need to be root. Sudo won't work. 

```
sudo su
```  
became  root
```
cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
```
Add something AT THE END of the file (if you use ">" instead of ">>" it delete the file with the new line). Cat will prommpt to enter something(copy and paste)
```
/usr/share/gdm/guest-session/guest-session-launch
```
once you have copied exit with Control+C

Make sure to create an autostart for the guess-session.

---

### Post by triunenature on 2011-08-03
> **fdrake said:**
> ```

$sudo su
#cat cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
>/usr/share/gdm/guest-session/guest-session-launch

```

these are scripts that the guess-session program uses.
to view the file of guess session 
```
ls /usr/share/gdm/guest-session/
```

```
less /usr/share/gdm/guest-session/guest-session-launch
```  
is the program that starts the guess session login (start up)


```
less /usr/share/gdm/guest-session/guest-session-cleanup.sh
```
when you log out from a session the guess-session program calls this script to clean up the tmp files and to delete the guess user. So what I did is to add a start up process before the cleanup end. Basically it's a loop. once you login in the student account the guess session will always restart at the end of the session.

to add the start up line at the end of this file you need to be root. Sudo won't work. 

```
sudo su
```  
became  root
```
cat >> /usr/share/gdm/guest-session/guest-session-cleanup.sh
```
Add something AT THE END of the file (if you use ">" instead of ">>" it delete the file with the new line). Cat will prommpt to enter something(copy and paste)
```
/usr/share/gdm/guest-session/guest-session-launch
```
once you have copied exit with Control+C

Make sure to create an autostart for the guess-session.

So, here is my cleanup script:

```

#!/bin/sh -e
# (C) 2008 Canonical Ltd.
# Author: Martin Pitt <martin.pitt@ubuntu.com>
# License: GPL v2 or later
#
# Clean up user and temporary home directory for guest session.
# Requires guest account name as $1.

USER="$1"

PWENT=`getent passwd "$USER"` || {
    echo "Error: invalid user $USER"
    exit 1
}
UID=`echo "$PWENT" | cut -f3 -d:`
HOME=`echo "$PWENT" | cut -f6 -d:`

if [ "$UID" -ge 500 ]; then
    echo "Error: user $USER is not a system user."
    exit 1
fi

if [ "${HOME}" = "${HOME#/tmp/}" ]; then
    echo "Error: home directory $HOME is not in /tmp/."
    exit 1
fi

# kill all remaining processes
while ps h -u "$USER" >/dev/null; do 
    killall -9 -u "$USER" || true
    sleep 0.2; 
done

umount "$HOME" || umount -l "$HOME" || true
rm -rf "$HOME"

# remove leftovers in /tmp
find /tmp -mindepth 1 -maxdepth 1 -uid "$UID" | xargs rm -rf || true

# remove gdm cache files
find /var/cache/gdm -mindepth 1 -maxdepth 1 -uid "$UID" | xargs rm -rf || true

deluser --system "$USER"

/usr/share/gdm/guest-session/guest-session-launch


```

Notice the last line is the launch.

But when I click logout, on the guest account, it brings up the student login, however it never restarts the guest account.

I have a startup item on the student account to launch guest-session.

---

### Post by fdrake on 2011-08-03
did you reboot to make sure that the changes made at the file take effect?

the file is identical to mine.

---

### Post by triunenature on 2011-08-03
> **fdrake said:**
> did you reboot to make sure that the changes made at the file take effect?

the file is identical to mine.

Yea, i restarted.  No effect.

How did you deal with the startup script.

I have a shell script, that launches gnome-session.  And the startup, launches that shell script.

Maybe that is the difference?

The only other thing, I may try to do a reinstall, to remove any custom configurations that i have created.  (which is ok, since this is the test machine)

---

### Post by fdrake on 2011-08-03
> **triunenature said:**
> Yea, i restarted.  No effect.

How did you deal with the startup script.

I have a shell script, that launches gnome-session.  And the startup, launches that shell script.

Maybe that is the difference?

The only other thing, I may try to do a reinstall, to remove any custom configurations that i have created.  (which is ok, since this is the test machine)

for the start up I just went to System > Preference > Add (name= guess-session, command= /usr/share/gdm/guest-session/guest-session-launch).
logoff and login.

edit: why do you need to start a script to start gnome? That is already handled bye the guest-session-launch script.

---

### Post by triunenature on 2011-08-04
> **fdrake said:**
> for the start up I just went to System > Preference > Add (name= guess-session, command= /usr/share/gdm/guest-session/guest-session-launch).
logoff and login.

edit: why do you need to start a script to start gnome? That is already handled bye the guest-session-launch script.

Whopps, i ment to say, guest-session.

But either way, once the guest logs off, the student is still logged on, and asked for a password

FIXED IT!!!!!

I just added:

```

sudo pkill -KILL -u student

```
to the end of the script.

```

#!/bin/sh -e
# (C) 2008 Canonical Ltd.
# Author: Martin Pitt <martin.pitt@ubuntu.com>
# License: GPL v2 or later
#
# Clean up user and temporary home directory for guest session.
# Requires guest account name as $1.

USER="$1"

PWENT=`getent passwd "$USER"` || {
    echo "Error: invalid user $USER"
    exit 1
}
UID=`echo "$PWENT" | cut -f3 -d:`
HOME=`echo "$PWENT" | cut -f6 -d:`

if [ "$UID" -ge 500 ]; then
    echo "Error: user $USER is not a system user."
    exit 1
fi

if [ "${HOME}" = "${HOME#/tmp/}" ]; then
    echo "Error: home directory $HOME is not in /tmp/."
    exit 1
fi

# kill all remaining processes
while ps h -u "$USER" >/dev/null; do 
    killall -9 -u "$USER" || true
    sleep 0.2; 
done

umount "$HOME" || umount -l "$HOME" || true
rm -rf "$HOME"

# remove leftovers in /tmp
find /tmp -mindepth 1 -maxdepth 1 -uid "$UID" | xargs rm -rf || true

# remove gdm cache files
find /var/cache/gdm -mindepth 1 -maxdepth 1 -uid "$UID" | xargs rm -rf || true

deluser --system "$USER"
sudo pkill -KILL -u student


```

---

### Post by triunenature on 2011-08-04
As for anyone looking to create a student or guest account here is the complete solution:

Create a guest user, but name is something OTHER than guest.  Because I am at a school, i named my user student, but visitor works just as well.  Make sure to click "Passwordless Login".  If this is going to be a public kiosk, or computer lab, also change to autologin (i set mine to 15 seconds, that way, if an admin needs to make changes, he or she can easily)

Edit this file: (requires root access)

/usr/share/gdm/guest-session/guest-session-cleanup.sh

I just used nano,  the last line should read:
```

sudo pkill -KILL -u student
## (or whatever you named your guest account)

```
The previous post, has the full script.


Go into the student/vistor account,

and go into startup applications (system -> preferences)

disable EVERYTHING.  Remember, this is just the shell of the account, and nothing you select will matter, just slow down the startup of the guest session.

Then add into startup applications:
```

/usr/share/gdm/guest-session/guest-session-launch

```
and name it anything.  I named mine studentaccess.

Done.
At minimum, logoff, and then log back into the student account.  For good measure, restart the computer.

---

### Post by psrdotcom on 2011-09-16
I would like to try .. let me see :confused:

---

### Post by youknowit on 2012-02-12
I am using 10.04 LTS. Somehow, adding the following line at the end of /usr/share/gdm/guest-session/guest-session-cleanup.sh did not work for me. After the guest session, I was back to the student (or whatever you named the account) login screen.
```

sudo pkill -KILL -u student
## (or whatever you named your guest account)

```

I solved this problem by writing a launcher script as follows:
```

#!/bin/bash
/usr/share/gdm/guest-session/guest-session-launch && /usr/bin/gnome-session-save --logout

```
I made this script executable (chmod +x) and used this file instead of "guest-session-launch" as the Startup Program for the account.

---

