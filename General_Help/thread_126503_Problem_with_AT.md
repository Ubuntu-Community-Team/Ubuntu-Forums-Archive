---
title: "Problem with AT"
date: 2006-02-06
forum: General Help
---

### Post by hfdragon on 2006-02-06
Hello, i'm having a problem with my ubuntu 5.10,

I'm trying tu use the AT command, and it doesn't seem to work.
Each time a create a new task with the command, at the time set for starting the task, nothing happens, and I keep getting this error in my syslog:

atd[<pid>]: File a000010116c118 is in wrong format - aborting

Anyone already had this problem ?

---

### Post by dcstar on 2006-02-06
[QUOTE=hfdragon]Hello, i'm having a problem with my ubuntu 5.10,

I'm trying tu use the AT command, and it doesn't seem to work.
Each time a create a new task with the command, at the time set for starting the task, nothing happens, and I keep getting this error in my syslog:

atd[<pid>]: File a000010116c118 is in wrong format - aborting

Anyone already had this problem ?[/QUOTE]
What does "atq" display for the task?

---

### Post by hfdragon on 2006-02-07
here it is :

```
christophe@christophe:~$ atq
24      2006-02-07 12:00 a christophe
25      2006-02-06 19:00 a christophe
25      2006-02-06 19:00 = christophe
26      2006-02-06 23:20 a christophe
26      2006-02-06 23:20 = christophe
24      2006-02-07 12:00 = christophe

```

These are the results of differents tries, none of wich made any result.

For example :
```
at 1200
>firefox
>(ctrl-d)
```

Everything seems ok, but at 1200, nothings happens, and i find the above error in my syslog.

---

### Post by z_diver on 2006-02-07
The AT daemon is not authenticated to use X.  Neither is cron.  I have heard of workarounds but not sure how to implement them.  I try to use command line tools that provide equivalent functionality.

---

### Post by hfdragon on 2006-02-07
[QUOTE=z_diver]The AT daemon is not authenticated to use X.  Neither is cron.  I have heard of workarounds but not sure how to implement them.  I try to use command line tools that provide equivalent functionality.[/QUOTE]

I'm not sure this is the reason why it is not working on my computer.

First, I had this problem when trying to use a program called fricorder (prog used to record ASDL TV), which is based on a python script using the AT command and using X. It is working on computers with ubuntu, bout not on mine... :-k 

But anyway, I tried this :
```
christophe@christophe:~$ at 2233
warning: commands will be executed using /bin/sh
at> wget http://ubuntuforums.org
at> <EOT>
job 29 at 2006-02-07 22:33

```
And i had this result in my syslog :
```

Feb  7 22:33:00 localhost atd[17173]: File a0001d0121c04d is in wrong format - aborting
```

And speaking of the syslog, it seems that all the tasks which are not working are still tried to be started by the at deamon, which is resulting of a huge CPU load and also a syslog containing (just for today) 4,000,000 + (yes, more than 4 millions !!!) lines with 
Feb  7 22:33:00 localhost atd[xxxxx]: File yyyyyyyyyyy is in wrong format - aborting :confused: :confused:

---

### Post by hfdragon on 2006-02-07
I'm looking if maybe there could be a permission/rights problem with my computer.

Can anyone tell me what are the normal permission setting for the :

/var/spool/cron
/var/spool/cron/atjobs
/var/spool/cron/atspool

directories ?

---

### Post by z_diver on 2006-02-07
[QUOTE=hfdragon]I'm looking if maybe there could be a permission/rights problem with my computer.

Can anyone tell me what are the normal permission setting for:

/var/spool/cron
/var/spool/cron/atjobs
/var/spool/cron/atspool[/QUOTE]
drwxr-xr-x  5 root   root    4096 2005-10-28 21:45 cron
drwxrwx--T  2 daemon daemon  4096 2006-01-27 13:34 atjobs
drwxrwx--T  2 daemon daemon  4096 2006-01-27 12:12 atspool

Hope that helps.

---

### Post by dcstar on 2006-02-08
[QUOTE=hfdragon]I'm not sure this is the reason why it is not working on my computer.

First, I had this problem when trying to use a program called fricorder (prog used to record ASDL TV), which is based on a python script using the AT command and using X. It is working on computers with ubuntu, bout not on mine... :-k 

But anyway, I tried this :
```
christophe@christophe:~$ at 2233
**warning: commands will be executed using /bin/sh**
at> wget http://ubuntuforums.org
at> <EOT>
job 29 at 2006-02-07 22:33

```
And i had this result in my syslog :
```

Feb  7 22:33:00 localhost atd[17173]: File a0001d0121c04d is in wrong format - aborting
```
......:[/QUOTE]
It is possible that some of the scripts you are trying to run need to use a different shell (like /bin/bash), and therefore fail when run under the "vanilla" /bin/sh.

This is just a guess, but it might give you some idea of where to look next.

I suppose you could try setting up a simple script that does work under /bin/sh and see if AT can run it ok.

---

### Post by bnutting on 2006-02-08
Well remember that at is run as the user that does the at command. So if you sudo the at command when you issue it it will be run as root, otherwise it is run by you. So do you have permissions to do what you want?

Also, if you want to see what the environment will look like and what exact commands will be run:
1. type atq to see what the job numbers are.
2. type at -c <jobnumber>

This will print out to stdout all the variables and the commands that will be issued.

Hope this helps,
Bryan

---

### Post by hfdragon on 2006-02-08
[QUOTE=z_diver]drwxr-xr-x  5 root   root    4096 2005-10-28 21:45 cron
drwxrwx--T  2 daemon daemon  4096 2006-01-27 13:34 atjobs
drwxrwx--T  2 daemon daemon  4096 2006-01-27 12:12 atspool

Hope that helps.[/QUOTE]

I've got exactly the same rights, so it's not coming from there :-(

Thanks anyway for your help.

But an yway, I tried something :
> christophe@christophe:/var/spool/cron$ sudo at 2344
Password:
warning: commands will be executed using /bin/sh
at> firefox
at> <EOT>
job 34 at 2006-02-08 23:44


If root could lauch this script, then maybe I have something...
And the result is : No message in the syslog, the task is disappearing from the list, and I get a mail :

```
From [email]root@localhost.loca[/email]ldomain  Wed Feb  8 23:44:01 2006
X-Original-To: root
Subject: Output from your job       34
To: [email]root@localhost.loca[/email]ldomain
Date: Wed,  8 Feb 2006 23:44:00 +0100 (CET)
From: [email]root@localhost.loca[/email]ldomain (root)

You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.

(firefox-bin:11190): Gtk-WARNING **: cannot open display:
```

So here is the problem about AT not having the right to use X.

But with root permission, the script is working... :-)
so I think I should keep looking in that direction...

[QUOTE=dcstar]It is possible that some of the scripts you are trying to run need to use a different shell (like /bin/bash), and therefore fail when run under the "vanilla" /bin/sh.

This is just a guess, but it might give you some idea of where to look next.

I suppose you could try setting up a simple script that does work under /bin/sh and see if AT can run it ok.[/QUOTE]

Yes, I wrote a simple script :
```
#!/bin/sh
firefox
```
And executing this script launches firefox without any problem. So I think I should have had the same result as above (as with usin sudo) with a simple AT hhmm >firefox, which in fact gives me the 'file is in wrong format - aborting' error message in my syslog.

So maybe it's not a problem about /bin/sh or /bin/bash...

I definitively think that it is a right problem... but where is it coming from...  I have no idea yet !!

---

### Post by dcstar on 2006-02-08
[QUOTE=hfdragon]......
And executing this script launches firefox without any problem. So I think I should have had the same result as above (as with usin sudo) with a simple AT hhmm >firefox, which in fact gives me the 'file is in wrong format - aborting' error message in my syslog.

So maybe it's not a problem about /bin/sh or /bin/bash...

I definitively think that it is a right problem... but where is it coming from...  I have no idea yet !![/QUOTE]
What happens when you do:

at hhmm /usr/bin/firefox

???

---

### Post by bnutting on 2006-02-09
So let me get this straight. One thing you are trying is to do is launch firefox at a given time and send it to your display? Correct? What happens if you in your current session:

1. Open a terminal window.
2. Type 'xhost +' (without the quotes abviously).
3. Schedule your at command to fire up firefox at your given time.
3a. In your at job, prior to firing up firefox enter in: export DISPLAY=:0 (That's zero not oh)
3b. End your at job with the usual CTRL+d.
4. Type 'atq' in your terminal window to get the job number.
5. Type 'at -c <yourjobnumber>' and view the output to make sure things look correct.
6. Leave everything open, don't breath on it or sneeze ;) 
7. See what happens.

Is the end result what you expect?

---

### Post by hfdragon on 2006-02-09
[QUOTE=dcstar]What happens when you do:

at hhmm /usr/bin/firefox

???[/QUOTE]

```
christophe@christophe:~$ at 1922
warning: commands will be executed using /bin/sh
at> /usr/bin/firefox
at> <EOT>
job 37 at 2006-02-09 19:22

```

And in my syslog :

```
Feb  9 19:22:00 localhost atd[13845]: File a000250121cace is in wrong format - aborting
```

No luck with this.. :-(

---

### Post by hfdragon on 2006-02-09
[QUOTE=bnutting]So let me get this straight. One thing you are trying is to do is launch firefox at a given time and send it to your display? Correct? What happens if you in your current session:

1. Open a terminal window.
2. Type 'xhost +' (without the quotes abviously).
3. Schedule your at command to fire up firefox at your given time.
3a. In your at job, prior to firing up firefox enter in: export DISPLAY=:0 (That's zero not oh)
3b. End your at job with the usual CTRL+d.
4. Type 'atq' in your terminal window to get the job number.
5. Type 'at -c <yourjobnumber>' and view the output to make sure things look correct.
6. Leave everything open, don't breath on it or sneeze ;) 
7. See what happens.

Is the end result what you expect?[/QUOTE]


No, i'm not trying to launch firefox.. it is just an (simple ?) example (maybe a bad one).

I'm trying in fact to use a program named fricorder which uses a python script to program the AT command to launch vlc to record TV.

And i'm quite sure fricorder is not working because I have a problem with AT.

Maybe I could try to use a non-X program to do my tests with AT ?

If I try :
```
christophe@christophe:~$ at 1928
warning: commands will be executed using /bin/sh
at> wget http://ubunutuforums.org
at> <EOT>
job 38 at 2006-02-09 19:28
christophe@christophe:~$

```

I still get my wrong file format error...

Anyway; I did your test :
```
christophe@christophe:~$ xhost +
access control disabled, clients can connect from any host
christophe@christophe:~$ at 1932
warning: commands will be executed using /bin/sh
at> export DISPLAY=:0
at> firefox
at> <EOT>
job 39 at 2006-02-09 19:32
christophe@christophe:~$ atq
39      2006-02-09 19:32 a christophe
christophe@christophe:~$ at -c 39
#!/bin/sh
# atrun uid=1000 gid=1000
# mail christophe 0
umask 22
SSH_AGENT_PID=9014; export SSH_AGENT_PID
DESKTOP_STARTUP_ID=; export DESKTOP_STARTUP_ID
GTK_RC_FILES=/etc/gtk/gtkrc:/home/christophe/.gtkrc-1.2-gnome2; export GTK_RC_FILES
WINDOWID=50331750; export WINDOWID
USER=christophe; export USER
LS_COLORS=no=00:fi=00:di=01\;34:ln=01\;36:pi=40\;33:so=01\;35:do=01\;35:bd=40\;33\;01:cd=40\;33\;01:or=40\;31\;01:ex=01\;32:\*.tar=01\;31:\*.tgz=01\;31:\*.arj=01\;31:\*.taz=01\;31:\*.lzh=01\;31:\*.zip=01\;31:\*.z=01\;31:\*.Z=01\;31:\*.gz=01\;31:\*.bz2=01\;31:\*.deb=01\;31:\*.rpm=01\;31:\*.jar=01\;31:\*.jpg=01\;35:\*.jpeg=01\;35:\*.gif=01\;35:\*.bmp=01\;35:\*.pbm=01\;35:\*.pgm=01\;35:\*.ppm=01\;35:\*.tga=01\;35:\*.xbm=01\;35:\*.xpm=01\;35:\*.tif=01\;35:\*.tiff=01\;35:\*.png=01\;35:\*.mov=01\;35:\*.mpg=01\;35:\*.mpeg=01\;35:\*.avi=01\;35:\*.fli=01\;35:\*.gl=01\;35:\*.dl=01\;35:\*.xcf=01\;35:\*.xwd=01\;35:\*.ogg=01\;35:\*.mp3=01\;35:\*.wav=01\;35:; export LS_COLORS
GNOME_KEYRING_SOCKET=/tmp/keyring-PjT1zC/socket; export GNOME_KEYRING_SOCKET
SSH_AUTH_SOCK=/tmp/ssh-AzVoQQ8976/agent.8976; export SSH_AUTH_SOCK
SESSION_MANAGER=unix/christophe:/tmp/.ICE-unix/8976; export SESSION_MANAGER
USERNAME=christophe; export USERNAME
DESKTOP_SESSION=default; export DESKTOP_SESSION
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games; export PATH
GDM_XSERVER_LOCATION=local; export GDM_XSERVER_LOCATION
PWD=/home/christophe; export PWD
LANG=fr_FR.UTF-8; export LANG
GDMSESSION=default; export GDMSESSION
HOME=/home/christophe; export HOME
SHLVL=1; export SHLVL
LANGUAGE=fr_FR:fr:en_GB:en; export LANGUAGE
GNOME_DESKTOP_SESSION_ID=Default; export GNOME_DESKTOP_SESSION_ID
LOGNAME=christophe; export LOGNAME
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Sk4QWm9IBH,guid=3d7aeb437742898c9d0a2daebd9f1800; export DBUS_SESSION_BUS_ADDRESS
LESSOPEN=\|\ /usr/bin/lesspipe\ %s; export LESSOPEN
LESSCLOSE=/usr/bin/lesspipe\ %s\ %s; export LESSCLOSE
COLORTERM=gnome-terminal; export COLORTERM
XAUTHORITY=/home/christophe/.Xauthority; export XAUTHORITY
cd /home/christophe || {
         echo 'Execution directory inaccessible' >&2
         exit 1
}
export DISPLAY=:0
firefox

```

And still the same error message in my syslog... :(

---

### Post by z_diver on 2006-02-09
> AT command to launch vlc to record TV
I still don't think that is possible.  Try this in a terminal.

sudo su
su daemon
vlc

Do you get this?
** CRITICAL **: Unable to open display

If so, maybe you can find a command line tool to record TV instead of using vlc.

---

### Post by hfdragon on 2006-02-09
[QUOTE=z_diver]I still don't think that is possible.  Try this in a terminal.

sudo su
su daemon
vlc

Do you get this?
** CRITICAL **: Unable to open display

If so, maybe you can find a command line tool to record TV instead of using vlc.[/QUOTE]

I'm not getting ** CRITICAL **, vlc is just starting ;) 

But anyway, I think my problem is just only about permissions.

I'va made some another tries, with a non-X program.

```
at 2000
>wget http://ubuntuforums.org
>(ctrl-d)
```

With this I get the error message in my syslog.

But with :
```
**sudo** at 2001
>wget http://ubuntuforums.org
>(ctrl-d)
```

It IS working, i get the index page of this site saved as a file... :p 

Anyone as an idea ?

---

### Post by z_diver on 2006-02-09
Well, I agree that you have a permissions issue.  I ran your tests on 2 ubuntu breezy machines and one Suse 9.2 and I get the expected behavior.  wget works fine when at is run using a normal user account and vlc cannot be run by daemon.

Is there any chance you ran a script that altered permissions?

---

### Post by hfdragon on 2006-02-09
[QUOTE=z_diver]Is there any chance you ran a script that altered permissions?[/QUOTE]

Yes, since i'm still new with linux and ubuntu (first install was only 10 month ago), I may have done something like that.. but I can't find where does my error comes from... ](*,)

---

### Post by hfdragon on 2006-02-10
Could anyone tell me which daemon I could try to launch as a standard user, to see if the problem comes from AT or from the deamon ?

---

### Post by hfdragon on 2006-02-10
I've made a few more tests, maybe with these informations, someone will be able to find a direction... ?

I created a new user (test), logged in this new user account and tested AT : everything is working fine.

I logged back on my normal user account, and tried this :
```
sudo -u test at 2110
>wget http://ubuntuforums.org
>(ctrl-d)
```

And.. it's working almost fine, just a small problem : test had not the right to write in my directories. But anyway, the script is working and I don't have the 'wrong file format' error. :D 

So I try this
```
sudo -u christophe at 2110
>wget http://ubuntuforums.org
>(ctrl-d)
```

And... It's not working : 'wrong file format error' :mad: 

So clearly, my 'normal' user accound has been prohibited the use of the at daemon or something like that, and I don't understand why (at.deny is blank)

Here are the two batch files created by AT and stored in /var/spool/cron/atjobs :

one with sudo -u test :
```
#!/bin/sh
# atrun uid=1002 gid=1002
# mail     test 0
umask 22
SSH_AGENT_PID=15863; export SSH_AGENT_PID
DESKTOP_STARTUP_ID=; export DESKTOP_STARTUP_ID
GTK_RC_FILES=/etc/gtk/gtkrc:/home/christophe/.gtkrc-1.2-gnome2; export GTK_RC_FILES
WINDOWID=46137446; export WINDOWID
USER=test; export USER
LS_COLORS=no=00:fi=00:di=01\;34:ln=01\;36:pi=40\;33:so=01\;35:do=01\;35:bd=40\;33\;01:cd=40\;33\;01:or=40\;31\;01:ex=01\;32:\*.tar=01\;31:\*.tgz=01\;31:\*.arj=01\;31:\*.taz=01\;31:\*.lzh=01\;31:\*.zip=01\;31:\*.z=01\;31:\*.Z=01\;31:\*.gz=01\;31:\*.bz2=01\;31:\*.deb=01\;31:\*.rpm=01\;31:\*.jar=01\;31:\*.jpg=01\;35:\*.jpeg=01\;35:\*.gif=01\;35:\*.bmp=01\;35:\*.pbm=01\;35:\*.pgm=01\;35:\*.ppm=01\;35:\*.tga=01\;35:\*.xbm=01\;35:\*.xpm=01\;35:\*.tif=01\;35:\*.tiff=01\;35:\*.png=01\;35:\*.mov=01\;35:\*.mpg=01\;35:\*.mpeg=01\;35:\*.avi=01\;35:\*.fli=01\;35:\*.gl=01\;35:\*.dl=01\;35:\*.xcf=01\;35:\*.xwd=01\;35:\*.ogg=01\;35:\*.mp3=01\;35:\*.wav=01\;35:; export LS_COLORS
GNOME_KEYRING_SOCKET=/tmp/keyring-q49VoU/socket; export GNOME_KEYRING_SOCKET
SSH_AUTH_SOCK=/tmp/ssh-VkUDS15825/agent.15825; export SSH_AUTH_SOCK
SESSION_MANAGER=unix/christophe:/tmp/.ICE-unix/15825; export SESSION_MANAGER
USERNAME=christophe; export USERNAME
DESKTOP_SESSION=default; export DESKTOP_SESSION
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin; export PATH
GDM_XSERVER_LOCATION=local; export GDM_XSERVER_LOCATION
PWD=/home/christophe; export PWD
LANG=fr_FR.UTF-8; export LANG
GDMSESSION=default; export GDMSESSION
HOME=/home/christophe; export HOME
SHLVL=1; export SHLVL
LANGUAGE=fr_FR:fr:en_GB:en; export LANGUAGE
GNOME_DESKTOP_SESSION_ID=Default; export GNOME_DESKTOP_SESSION_ID
LOGNAME=test; export LOGNAME
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-OYKi57Ehxj,guid=89f0ec4378b6e6f2e212194343e05700; export DBUS_SESSION_BUS_ADDRESS
LESSOPEN=\|\ /usr/bin/lesspipe\ %s; export LESSOPEN
LESSCLOSE=/usr/bin/lesspipe\ %s\ %s; export LESSCLOSE
COLORTERM=gnome-terminal; export COLORTERM
XAUTHORITY=/home/christophe/.Xauthority; export XAUTHORITY
SUDO_COMMAND=/usr/bin/at\ 2110; export SUDO_COMMAND
SUDO_USER=christophe; export SUDO_USER
SUDO_UID=1000; export SUDO_UID
SUDO_GID=1000; export SUDO_GID
cd /home/christophe || {
	 echo 'Execution directory inaccessible' >&2
	 exit 1
}
wget http://ubuntuforums.org


```

And the one with sudo -u christophe
```
#!/bin/sh
# atrun uid=1000 gid=1000
# mail christophe 0
umask 22
SSH_AGENT_PID=15863; export SSH_AGENT_PID
DESKTOP_STARTUP_ID=; export DESKTOP_STARTUP_ID
GTK_RC_FILES=/etc/gtk/gtkrc:/home/christophe/.gtkrc-1.2-gnome2; export GTK_RC_FILES
WINDOWID=46137446; export WINDOWID
USER=christophe; export USER
LS_COLORS=no=00:fi=00:di=01\;34:ln=01\;36:pi=40\;33:so=01\;35:do=01\;35:bd=40\;33\;01:cd=40\;33\;01:or=40\;31\;01:ex=01\;32:\*.tar=01\;31:\*.tgz=01\;31:\*.arj=01\;31:\*.taz=01\;31:\*.lzh=01\;31:\*.zip=01\;31:\*.z=01\;31:\*.Z=01\;31:\*.gz=01\;31:\*.bz2=01\;31:\*.deb=01\;31:\*.rpm=01\;31:\*.jar=01\;31:\*.jpg=01\;35:\*.jpeg=01\;35:\*.gif=01\;35:\*.bmp=01\;35:\*.pbm=01\;35:\*.pgm=01\;35:\*.ppm=01\;35:\*.tga=01\;35:\*.xbm=01\;35:\*.xpm=01\;35:\*.tif=01\;35:\*.tiff=01\;35:\*.png=01\;35:\*.mov=01\;35:\*.mpg=01\;35:\*.mpeg=01\;35:\*.avi=01\;35:\*.fli=01\;35:\*.gl=01\;35:\*.dl=01\;35:\*.xcf=01\;35:\*.xwd=01\;35:\*.ogg=01\;35:\*.mp3=01\;35:\*.wav=01\;35:; export LS_COLORS
GNOME_KEYRING_SOCKET=/tmp/keyring-q49VoU/socket; export GNOME_KEYRING_SOCKET
SSH_AUTH_SOCK=/tmp/ssh-VkUDS15825/agent.15825; export SSH_AUTH_SOCK
SESSION_MANAGER=unix/christophe:/tmp/.ICE-unix/15825; export SESSION_MANAGER
USERNAME=christophe; export USERNAME
DESKTOP_SESSION=default; export DESKTOP_SESSION
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin; export PATH
GDM_XSERVER_LOCATION=local; export GDM_XSERVER_LOCATION
PWD=/home/christophe; export PWD
LANG=fr_FR.UTF-8; export LANG
GDMSESSION=default; export GDMSESSION
HOME=/home/christophe; export HOME
SHLVL=1; export SHLVL
LANGUAGE=fr_FR:fr:en_GB:en; export LANGUAGE
GNOME_DESKTOP_SESSION_ID=Default; export GNOME_DESKTOP_SESSION_ID
LOGNAME=christophe; export LOGNAME
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-OYKi57Ehxj,guid=89f0ec4378b6e6f2e212194343e05700; export DBUS_SESSION_BUS_ADDRESS
LESSOPEN=\|\ /usr/bin/lesspipe\ %s; export LESSOPEN
LESSCLOSE=/usr/bin/lesspipe\ %s\ %s; export LESSCLOSE
COLORTERM=gnome-terminal; export COLORTERM
XAUTHORITY=/home/christophe/.Xauthority; export XAUTHORITY
SUDO_COMMAND=/usr/bin/at\ 2115; export SUDO_COMMAND
SUDO_USER=christophe; export SUDO_USER
SUDO_UID=1000; export SUDO_UID
SUDO_GID=1000; export SUDO_GID
cd /home/christophe || {
	 echo 'Execution directory inaccessible' >&2
	 exit 1
}
wget http://ubuntuforums.org


```

I can't see any difference (exect for the user names) !!! :confused: :confused: :confused: :confused:

---

### Post by dcstar on 2006-02-10
[QUOTE=hfdragon]I've made a few more tests, maybe with these informations, someone will be able to find a direction... ?

I created a new user (test), logged in this new user account and tested AT : everything is working fine.
.......
[/QUOTE]
Log in as each user, and have a look at the result of running "groups".

---

### Post by hfdragon on 2006-02-10
[QUOTE=dcstar]Log in as each user, and have a look at the result of running "groups".[/QUOTE]

```
christophe@christophe:~$ groups
christophe adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
christophe@christophe:~$ sudo -u test groups
test adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner
```

No big differences.... ?
Being in the admin group or not being in fax or tape group ?

:-k :-k

---

