---
title: "Sudo or user login not working (fresh install)"
date: 2011-08-17
forum: General Help
---

### Post by maddox on 2011-08-17
Hi,

I have this weird problem after a fresh install of Ubuntu 11.04:


I can enter desktop using autologin but if i open a terminal i cant run anything as superuser
tried:

sudo -i
sudo su
sudo <command>
gksudo <command>

i get somthing like: error, invalid password etc etc 3 incorrect login attemtps

Also if i ALT+F2 or close gnome session i cannot login back with my username, same error


notes:
1. the password is right, i did a second install of ubuntu to make sure it was not my mistake

2. groups seems ok, user is in admin groups

3. I have a similar error, same computer but on an old installation that i´´ve updated since ubuntu 9.04 to 10.04, then 11.04 but. But here if i try the password a couple of times then i get it working



Could it be the keyboard?? When i type on a terminal seems ok...

---

### Post by spiceminesofkessel on 2011-08-17
Am I correct in understanding that you have reinstalled Ubuntu and the problem persists? If that be the case, I find that to be simply bizarre. That would lead me to think that the issue is with something other than the OS. It might be the keyboard. That might seem trivial, but I have a keyboard on one of my computers that acts up randomly, which causes me to mistype passwords. That's at least a beginning. Other than suggesting you try a different keyboard, I can't offer much in advice other than some nitpicking on some little things, such as try a different USB port, etc.

---

### Post by jfed on 2011-08-17
I agree, it could very well be the keyboard. I run arch on an old machine from 95, and one day it decided to just not log me in, no matter how many times I tried, it would just not work. I later then realized that the num row just kicked the bucket on me, and the only way to enter numbers was to use the numpad. So it could be the keyboard, haha and if that still doesn't work, re-download and burn the ISO and try again I guess.. =/

---

### Post by maddox on 2011-08-17
Ok, so its not the keyboard as i changed it.

Also i tried to install Kubuntu 11.04 this time and i have the same problem over and over again.

ERRORS:
maddox@Media-BOX:~$ sudo -i
[sudo] password for maddox: 
Sorry, try again.
[sudo] password for maddox: 
Sorry, try again.
[sudo] password for maddox: 
Sorry, try again.
sudo: 3 incorrect password attempts
maddox@Media-BOX:~$

GROUPS:
maddox@Media-BOX:~$ groups 
maddox adm dialout cdrom plugdev lpadmin admin sambashare

SYSLOG:
[http://pastebin.com/1MjnyN6h](http://pastebin.com/1MjnyN6h)

AUTH.LOG:
```

Aug 17 23:59:11 Media-BOX kdm: :0[1037]: pam_unix(kdm-np:session): session opened for user maddox by (uid=0)
Aug 17 23:59:11 Media-BOX kdm: :0[1037]: pam_ck_connector(kdm-np:session): nox11 mode, ignoring PAM_TTY :0
Aug 18 00:00:26 Media-BOX polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.35 [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Aug 18 00:04:28 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:04:40 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/bin/bash
Aug 18 00:04:54 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:05:05 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:05:09 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:05:22 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:05:26 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:05:39 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:05:44 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:05:55 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:05:59 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:06:12 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:06:50 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser=maddox rhost=  user=maddox
Aug 18 00:07:13 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/maddox ; USER=root ; COMMAND=/usr/bin/synaptiks
Aug 18 00:07:22 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:07:36 Media-BOX login[771]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty2 ruser= rhost=  user=maddox
Aug 18 00:07:39 Media-BOX login[771]: FAILED LOGIN (1) on '/dev/tty2' FOR 'maddox', Authentication failure
Aug 18 00:07:43 Media-BOX login[771]: pam_unix(login:auth): check pass; user unknown
Aug 18 00:07:43 Media-BOX login[771]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty2 ruser= rhost= 
Aug 18 00:07:46 Media-BOX login[771]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 18 00:07:52 Media-BOX login[771]: FAILED LOGIN (3) on '/dev/tty2' FOR 'maddox', Authentication failure
Aug 18 00:07:59 Media-BOX login[771]: FAILED LOGIN (4) on '/dev/tty2' FOR 'maddox', Authentication failure
Aug 18 00:08:05 Media-BOX login[771]: FAILED LOGIN (5) on '/dev/tty2' FOR 'maddox', Authentication failure
Aug 18 00:08:05 Media-BOX login[771]: TOO MANY LOGIN TRIES (5) on '/dev/tty2' FOR 'maddox'
Aug 18 00:08:05 Media-BOX login[771]: pam_mail(login:session): pam_putenv: delete non-existent entry; MAIL
Aug 18 00:08:05 Media-BOX login[771]: pam_unix(login:session): session closed for user maddox
Aug 18 00:08:05 Media-BOX login[771]: PAM 3 more authentication failures; logname=LOGIN uid=0 euid=0 tty=/dev/tty2 ruser= rhost=  user=maddox
Aug 18 00:08:05 Media-BOX login[771]: PAM service(login) ignoring max retries; 4 > 3
Aug 18 00:12:56 Media-BOX kdm: :0[1035]: pam_unix(kdm-np:session): session opened for user maddox by (uid=0)
Aug 18 00:12:56 Media-BOX kdm: :0[1035]: pam_ck_connector(kdm-np:session): nox11 mode, ignoring PAM_TTY :0
Aug 18 00:13:15 Media-BOX dbus-daemon: [system] Rejected send message, 7 matched rules; type="method_call", sender=":1.26" (uid=1000 pid=1320 comm="/usr/bin/plasma-desktop ") interface="org.freedesktop.NetworkManager" member="Sleep" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=418 comm="NetworkManager "))
Aug 18 00:13:31 Media-BOX polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.35 [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Aug 18 00:14:04 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:14:17 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/bin/su
Aug 18 00:17:01 Media-BOX CRON[1600]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 00:17:01 Media-BOX CRON[1600]: pam_unix(cron:session): session closed for user root
Aug 18 00:17:32 Media-BOX sudo: pam_unix(sudo:auth): authentication failure; logname=maddox uid=0 euid=0 tty=/dev/pts/1 ruser=maddox rhost=  user=maddox
Aug 18 00:17:43 Media-BOX sudo:   maddox : 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/maddox ; USER=root ; COMMAND=/bin/bash

```

---

### Post by maddox on 2011-08-22
*bump*

---

