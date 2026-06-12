---
title: "I suddenly can't login anymore"
date: 2010-04-18
forum: General Help
---

### Post by PHaLaNX on 2010-04-18
Hello,

I've been using 9.10 for a couple of months now. Today while I was working I got a warning saying that the disk was full, and suddenly I couldn't do anything, everything just locked up. 

So I hit the reset button, and when it opened again it now shows me a KDE login screen (which I shouldn't be getting, since I was using auto-login), and it doesn't accept my username and password. 

The only way I can login now is choosing the recovery mode in the grub list, dropping to root shell, logging in with my username and typing startx. And sound also doesn't work if I login this way, for some reason. 

I got 4 seperate entries in the grub list for a long time, two different kernel versions and their recovery modes. It used to do the exact same thing when I chose the lower version one, but now the newer one does it too. 

How can I get rid of this login screen? I'm figuring if I can login properly then the sound issue will go away too, hopefully. 

Any help will be greatly appreciated

Thanks

Edit: It is like the system is trying to login the first time, but it fails and it falls to this login screen. Then it actually accepts my password but it can't go further and comes back to the same screen.

---

### Post by klemes on 2010-04-18
Probably you are facing the possibility of data corruption due to low free disk capacity.
You could try to make some space in your /home and/or in your root partition.
Use ```
df -h
```to determine your hard drive free space status.

---

### Post by wilee-nilee on 2010-04-18
If your hard drive is full you need to remove stuff, this can be done with a live cd if you can't get back in.

---

### Post by jkxx on 2010-04-18
From your post it sounds like your file system is full - that can cause all kinds of problems including what you posted. If you can get to a shell you could try the 'df' command to see how much free space is left. The first line should show you your root (/) partition and how much of it is used. I suspect you'll see 100% there. If you do you may need to delete some files to free enough space to log in.

I don't want to post any commands that would allow you to delete anything so do the above first and post the results first.

---

### Post by PHaLaNX on 2010-04-18
**klemes, wilee-nilee, jkxx**

I had less than 200 MB's but now I freed some and I have more than 15 GB's free. Nothing changed though. Still can't login properly.

---

### Post by klemes on 2010-04-18
What are you using as login manager KDM or GDM?Probably KDM since it's Kubuntu as the title suggests.
One quick fix could be:

```
sudo apt-get install --reinstall kdm
```Try it and post us how it goes and we 'll see from there.

---

### Post by PHaLaNX on 2010-04-18
OK, klemes, I did it and nothing changed. Still the same login screen. The screen goes white for a second when I enter the password and then it's back again. Same white screen also appears before the login screen.

Maybe like a graphics problem? Shall I post some logs? If so which ones?

---

### Post by klemes on 2010-04-18
> **PHaLaNX said:**
> OK, klemes, I did it and nothing changed. Still the same login screen. The screen goes white for a second when I enter the password and then it's back again. Same white screen also appears before the login screen.

Maybe like a graphics problem? Shall I post some logs? If so which ones?

I don't think it's a grahical problem since you said that you are able to access X by typing startx,so we are moving away from this.
It's not also a password related problem since you are able to log-in in console-mode.
Try this from the console :

sudo /etc/init.d/kdm restart

or 

sudo restart kdm

and see what happens also note for any errors or notifications.

Also try to login as root or even create a new user and log-in using the new account this will tell us if it is a system wide fault or just related to your user account.

---

### Post by klemes on 2010-04-18
Oh, and I just noticed that you said in your first post that you used auto log-in,so please try to disable this before doing anything further.

---

### Post by PHaLaNX on 2010-04-18
I disabled auto-login first, then created a new user. It logins fine with it. So I think it's just my account. Also restarting kdm works fine, no errors. What might be wrong with my account?

---

### Post by klemes on 2010-04-18
Some setup-up files in your home directory obviously become corrupted,trouble is I dont't know which ones ,but my guess is that they are located in the .kde(notice the dot in front of the kde)hidden directory.Try to back it up in some way (ie mv .kde .kde.bak) and then try to login  again.Your .kde directory will be formated again but you will have lost all your personalizations and settings (ie wallpaper,kde application settings and so on).
I would personally would do it and have done it as a last resort if nothing else worksbut better wait a little longer for some possible more specific advice on this.In any case it's up to you..

---

### Post by klemes on 2010-04-18
Some more investigation into your problem showed me that there is a file 

/home/your_username/.kde/share/config/kdm

which quiet possibly could be the offending file.

Try to back it up first and then erase the original and then try to login again.

---

### Post by PHaLaNX on 2010-04-18
I looked and there was no file like that in ~/.kde/share/config, so I backed up .kde and deleted it and nothing happened, still can't login. 

Something happening just as it's trying to login and no errors or anything. I would say it might be in the logs somewhere but I don't know where to look at.

---

### Post by klemes on 2010-04-18
/var/log/kdm.log would be a good place to start.
But I find it very strange that you are still not able to login properly after erasing the .kde folder..
Have you any other window managers installed? ie gnome,openbox,fluxbox,lxdm????
If so have you tried to choose one of them from the kdm menu to see if you are able to login into one of them???

---

### Post by PHaLaNX on 2010-04-18
No, I only have kde. Here is the /var/log/kdm.log file

```
********************************************************************************
Note that your system uses syslog. All of kdm's internally generated messages
(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 13:38:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 13:39:51 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 14:03:30 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 14:24:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 16:15:16 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 16:47:20 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 18 16:49:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x27a400]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x1247700]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0x114) [0x120a2b4]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x60) [0x1208050]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x1259bc6]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x2ee) [0x1258f6e]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x42) [0x1233b22]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x77) [0x1231e57]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x45) [0x1230015]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x39) [0x12300f9]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x199) [0x12303c9]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x120630d]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x4a) [0x1205e6a]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0xaf) [0x11c129f]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x5a) [0x117b94a]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11c818e]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11c6071]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0x141) [0x11c6271]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0xb2) [0x11c6e12]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x41a) [0x11c4f6a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x1178) [0x117caf8]
23: /usr/bin/X(InitOutput+0x4e9) [0x80b05b9]
24: /usr/bin/X(main+0x1cb) [0x807234b]
25: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x68cb56]
26: /usr/bin/X [0x80719c1]
Saw signal 8.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 18 16:49:25 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x904400]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11bd700]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0x114) [0x11802b4]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x60) [0x117e050]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11cfbc6]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x2ee) [0x11cef6e]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x42) [0x11a9b22]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x77) [0x11a7e57]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x45) [0x11a6015]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x39) [0x11a60f9]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x199) [0x11a63c9]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x117c30d]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x4a) [0x117be6a]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0xaf) [0x113729f]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x5a) [0x10f194a]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x113e18e]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x113c071]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0x141) [0x113c271]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0xb2) [0x113ce12]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x41a) [0x113af6a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x1178) [0x10f2af8]
23: /usr/bin/X(InitOutput+0x4e9) [0x80b05b9]
24: /usr/bin/X(main+0x1cb) [0x807234b]
25: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x364b56]
26: /usr/bin/X [0x80719c1]
Saw signal 8.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 18 16:49:41 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x443400]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x123a700]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0x114) [0x11fd2b4]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x60) [0x11fb050]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x124cbc6]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x2ee) [0x124bf6e]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x42) [0x1226b22]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x77) [0x1224e57]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x45) [0x1223015]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x39) [0x12230f9]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x199) [0x12233c9]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11f930d]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x4a) [0x11f8e6a]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0xaf) [0x11b429f]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x5a) [0x116e94a]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11bb18e]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11b9071]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0x141) [0x11b9271]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0xb2) [0x11b9e12]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x41a) [0x11b7f6a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x1178) [0x116faf8]
23: /usr/bin/X(InitOutput+0x4e9) [0x80b05b9]
24: /usr/bin/X(main+0x1cb) [0x807234b]
25: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x27fb56]
26: /usr/bin/X [0x80719c1]
Saw signal 8.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sun Apr 18 16:49:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x60c400]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11d2700]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0x114) [0x11952b4]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x60) [0x1193050]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x11e4bc6]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x2ee) [0x11e3f6e]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x42) [0x11beb22]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x77) [0x11bce57]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x45) [0x11bb015]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x39) [0x11bb0f9]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x199) [0x11bb3c9]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x119130d]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x4a) [0x1190e6a]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0xaf) [0x114c29f]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x5a) [0x110694a]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x115318e]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x1151071]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0x141) [0x1151271]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0xb2) [0x1151e12]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x41a) [0x114ff6a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x1178) [0x1107af8]
23: /usr/bin/X(InitOutput+0x4e9) [0x80b05b9]
24: /usr/bin/X(main+0x1cb) [0x807234b]
25: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x388b56]
26: /usr/bin/X [0x80719c1]
Saw signal 8.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 16:51:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 17:31:38 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 17:37:44 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 17:39:12 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 84625479301 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=bb48d03c-9542-4cec-bee2-b71b6d4fa491 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 18:44:31 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```

May this be the problem?

```
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
```

---

### Post by klemes on 2010-04-18
Well maybe you were right maybe it is an xorg.conf issue.Tell me are you using an ATI video card?And how was ,I mean with what method,was your xorg.conf file generated?
Try this also:

Edit your /etc/X11/xorg.conf file and try to comment out the line if it exists starting with BusID in the Driver Section,then restart X.

---

### Post by Serpher on 2010-04-18
Perhaps reinstall X11?

---

### Post by jkxx on 2010-04-18
That is quite odd... Here is something you could try although I'm not sure it would help - but it might since I see a core dump/crash in that log.

Log in as root and go into the directory /etc/X11/ - backup the xorg.conf file before you do anything to it, then open the file in nano or your preferred editor.

Find the part which reads 
Section "Device"

there should be a line which starts with the word Driver; change it so it says 

Driver "vesa"

then save the file and reboot/restart X. Are you able to log in now?

EDIT: I see Klemes already had you try that - follow his advice first before trying this.

---

### Post by PHaLaNX on 2010-04-18
OK, will try these right now. 

In the mean time I deleted the xorg.conf and created another one with aticonfig (yes, I have an ATI card), but no difference so far. 

Will try to comment out that line now.

Edit: Tried commenting out BusID and then Driver one by one, no change. Trying vesa.

---

### Post by klemes on 2010-04-18
Could you supply your ~/.bashrc ?I am beginning to think that this is the source of your problem for not being able to login via kdm.

---

### Post by PHaLaNX on 2010-04-18
Vesa didn't work, all I got was a blanking cursor after I entered the pessword. Isn't xorg.conf used by all the users, anyway? I'm able to login with another account, so that doesn't make sense.

Here is .bashrc:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

It was last modified more than 4 months ago, fyi.

I don't understand why hard disk being full for a couple of minutes would cause all these problems.

---

### Post by klemes on 2010-04-18
Your .bashrc file seems fine,that's not the problem.
That's it.One last guess and I am giving up for now.
Have a look at your ~/.profile file especially in the PATH section and If that seems alright then I don't know what could be wrong with your 'buntu....

---

### Post by PHaLaNX on 2010-04-18
~/.profile looks OK too. Thanks for trying anyway. 

Any more suggestions, anyone?

Edit: I thought I might add the file:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

---

### Post by PHaLaNX on 2010-04-18
At least the new user works. So I can just go on with that one. But it would be good to fix the existing one right now. 

I'm thinking maybe it was the reset I did after the lock up caused all this.

---

### Post by PHaLaNX on 2010-04-18
Anyone has suggestions I might try before deleting this account?

---

### Post by PHaLaNX on 2010-04-19
Up, will wait for today, then give up.

---

### Post by Chronon on 2010-04-19
What does your partition table look like?  Is it possible that a partition is full even though there's plenty of free space on the disk?

---

### Post by PHaLaNX on 2010-04-19
No, the root partition itself has 15 GB of free space now.

---

