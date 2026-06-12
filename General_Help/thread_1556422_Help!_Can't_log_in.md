---
title: "Help! Can't log in"
date: 2010-08-19
forum: General Help
---

### Post by bilkay on 2010-08-19
After trying a "fix" I found on another thread, nobody can log into my laptop! After each attempt, a single message shows up in /var/log/messages:

Aug 19 11:44:46 ubuntu kernel: [   52.459328] type=1503 audit(1282232686.548:17):  operation="open" pid=1613 parent=1399 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/${USER}/.profile"

```
$ cd
$ ls -l .profile
-rw-r--r-- 1 ${USER} ${USER} 702 2010-08-17 16:02 .profile

$ cd /usr/share/gdm/guest-session
$ ls -l Xsession
-rwxr-xr-x 1 root root 91 2010-04-14 19:24 Xsession
```Background:

The initial problem was an error message on login: Can't update /home/${USER}/.ICEauthority, and it was taking a long time to get past it.

Here's the "fix" ([http://ubuntuforums.org/showthread.php?t=1366173&highlight=.ICEauthority):]("http://ubuntuforums.org/showthread.php?t=1366173&highlight=.ICEauthority%29:")

> **Flos Headford said:**
> This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to  something appropriate (I used 755) and make sure all directories can be  listed with the "ls" command. Then remove nautilus with ```
sudo  apt-get remove nautilus
``` and delete the .ICEauthority entry in  $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo  shutdown -r now
``` When you choose the same option on boot-up, from  the command line you can use ```
sudo apt-get install nautilus
 sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
with thanks to all who helped me,
Phil

The only thing I did differently was I booted into recovery mode from the grub menu rather than from live CD.

---

### Post by bilkay on 2010-08-19
Further note: The gdm login screen comes up, but after login attempt, black screen with text flashes up too fast to read, then returns to gdm login screen.

---

### Post by mikewhatever on 2010-08-19
It looks like you've picked very poor instructions. I am going to report that post as potentially harmful and ask it edited, as deleting .ICEauthority is a bad move.
Take a look at a proper explanation -> [http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985).

---

### Post by bilkay on 2010-08-19
> **mikewhatever said:**
> It looks like you've picked very poor instructions. I am going to report that post as potentially harmful and ask it edited, as deleting .ICEauthority is a bad move.
Take a look at a proper explanation -> [http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985).
Okay, we can all agree that I screwed up by assuming that if something worked for someone else, it would work for me. But what now?

BTW, I tried restoring the ~/.ICEauthority files from backup with no luck.

---

### Post by bilkay on 2010-08-19
```
$ cd
$ cat .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open /home/${USER}/.profile
```

I don't see any reason why ~/.profile can't be opened.

```
$ cd
$ ls -l .profile
-rw-r--r-- 1 ${USER} ${USER} 702 2010-08-17 16:02 .profile
```

---

### Post by bilkay on 2010-08-19
It's crashing out of /etc/gdm/Xsession in this loop:

if [ -d /etc/X11/Xsession.d ]; then
    for i in `ls /etc/X11/Xsession.d/` ; do
        if [ -r "/etc/X11/Xsession.d/$i" ] && expr "$i" : '^[[:alnum:]_-]\+$' > /dev/null; then
            . "/etc/X11/Xsession.d/$i"
        fi
    done
fi

In script 99x11-common_start:

exec $STARTUP

---

### Post by bilkay on 2010-08-19
At this point, STARTUP = /usr/bin/ssh-agent   /usr/bin/dbus-launch --exit-with-session /usr/share/gdm/guest-session/Xsession

It's not getting to the script /gdm/guest-session/Xsession. Now I'm stumped

---

### Post by mjones1984 on 2010-09-10
I too followed Flos Headford's advice ([http://ubuntuforums.org/showthread.php?t=1366173](http://ubuntuforums.org/showthread.php?t=1366173)) and now cannot login.  From what I can tell, running Klamav or clamav with 'sudo' caused the issue in the first place.  To clear the "could not update .ICEauthority" message I used ```
sudo chown [username]:[username] /home/[username]/.ICEauthority
sudo chmod 664 /home/[username]/.ICEauthority
``` (where [username] is my username) and then restarted.  This let me get into gnome but I couldn't interact with anything even though things were running (i.e. CPU usage graph).  Then I followed Flos Headford's advice and found myself at a login screen that would point back at itself on login (accepting my username and password but falling back to the login screen on success).  For anyone considering deleting .ICEauthority and reinstalling nautilus, **do this as a last resort**.  I was running Ubuntu 10.04LTS at the time and will resort to reinstalling the whole system as a result.

---

### Post by bilkay on 2010-09-10
What I find disquieting is that a single, seemingly innocuous file deletion can cause so much havoc, and based on the lack of responses, can't be remedied.

---

### Post by zuerston on 2010-09-10
Please use clamtk 4.15 GUI and not have these problems.

---

