---
title: "KDM will not log me in"
date: 2011-06-20
forum: General Help
---

### Post by timmy366 on 2011-06-20
Hi all. I have a problem with KDM. No matter what I do, it will not give me access to my desktop. (Yes, I have entered the correct password, and I know that because when I intentionally enter a wrong one, I get red lines saying so). I have tried in recovery mode, other kernels, and the failsafe session. Console login does work. I have seen another similar thread and followed some instructions, but it was about GDM and it didn't work out. I have ran genkdmconf, but to no avail (except it gave me a new face icon :)). My other operating systems (Windows Vista and Ubuntu 11.04) do work normally. [EDIT: I do have an idea what's causing this because yesterday I flashed my BIOS from A11 to A17. I don't think this is the cause of the problem though, but some of you may disagree]. Of course it's not my first preference, but *if* a reinstall is necessary, I am one of the lucky few with a seperate /home ;).

Any help would be *greatly* appreciated...

---

### Post by gmargo on 2011-06-20
No solution, but a couple of random ideas: 

Check the log files (/var/log/kdm.log*, syslog, auth.log, or any recently changed log file)

Rename the $HOME/.kde/ directory temporarily.

It shouldn't be a BIOS flashing problem... Unless it was working before you flashed!

---

### Post by timmy366 on 2011-06-21
Sorry, didn't work. I also looked in /var/tmp and found some 'kdecache-username' folders there, and changed their names to see what happened, but nothing. I believe there was a folder named /var/pid too? I couldn't find it, but seemed logical to look in...
Thanks for the reply anyway ;)

---

### Post by timmy366 on 2011-06-25
Guess I'm going to have to reinstall? :(

---

### Post by gmargo on 2011-06-25
I'm surprised you haven't already.  One more thought... You don't have any weird characters in your username or password do you?

---

### Post by timmy366 on 2011-06-25
I've been using my other Ubuntu all the time. Getting tired of it now, want KDE back...
No special characters in the password...

---

### Post by Zorael on 2011-06-25
**/var/log/kdm.log** should be the file you want, yes. Are you sure it's not there?

Also make sure your disks aren't full. It fails silently like that if there isn't enough space.

---

### Post by timmy366 on 2011-06-27
Disks are almost empty... But here's something interesting. I reinstalled yesterday, and guess what? Exact same problem. I have a separate /home, but I did remove all the hidden files in my home folder. I'll try to reinstall again now...

---

### Post by timmy366 on 2011-06-27
...and guess what? Same problem.
The /var/log/kdm.log file says the following:
```

********************************************************************************
Note that your system uses syslog. All of kdm's internally generated messages
(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux laptop-tiemen 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=89e5f6a0-21c2-42be-a045-3ecd9c78bdc5 ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 27 17:47:51 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1265195939/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1641715114/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
 ddxSigGiveUp: Closing log
```
Is it possible that KDM just doesn't like the new A17 BIOS? I can downgrade to A11 if necessary.

---

