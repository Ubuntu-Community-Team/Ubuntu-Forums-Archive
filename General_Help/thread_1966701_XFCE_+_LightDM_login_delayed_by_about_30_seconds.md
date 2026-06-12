---
title: "XFCE + LightDM login delayed by about 30 seconds"
date: 2012-04-27
forum: General Help
---

### Post by J V on 2012-04-27
Logging in via LightDM in xubuntu 12.04 has a large delay (Longer than the rest of the total boot time)

When I log in the default wallpaper and mouse are shown while no processes do anything (Top on tty shows init as highest CPU using process)

Several seconds later (Usually about half a minute) the system pretty much instantly loads the desktop and everything works.

Logging out produces a black unresponsive screen for a similar time as the wallpaper during login, followed by LightDM not listing my user, and not allowing me to login via "Other" either.


/var/log/auth.log:
```
Apr 27 15:11:34 fatherboard lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr 27 15:11:34 fatherboard lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 27 15:11:34 fatherboard dbus[763]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.14" (uid=104 pid=1453 comm="/usr/sbin/lightdm-gtk-greeter ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.12" (uid=0 pid=1374 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr 27 15:11:34 fatherboard lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "j"
Apr 27 15:11:43 fatherboard lightdm: pam_unix(lightdm:session): session closed for user lightdm
Apr 27 15:12:58 fatherboard lightdm: pam_unix(lightdm:session): session opened for user j by (uid=0)
Apr 27 15:12:58 fatherboard lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 27 15:12:59 fatherboard polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.21 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

```
/var/log/lightdm/lightdm.log
```
[+1.42s] DEBUG: Greeter start authentication for j
[+1.42s] DEBUG: Started session 1635 with service 'lightdm', username 'j'
[+1.42s] DEBUG: Session 1635 got 1 message(s) from PAM
[+1.42s] DEBUG: Prompt greeter with 1 message(s)
[+9.96s] DEBUG: Continue authentication
[+10.46s] DEBUG: Session 1635 authentication complete with return value 0: Success
[+10.46s] DEBUG: Authenticate result for user j: Success
[+10.46s] DEBUG: User j authorized
[+10.47s] DEBUG: Greeter sets language en_US
[+10.47s] WARNING: Could not call SetLanguage: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so language not saved
[+10.47s] DEBUG: Greeter requests session xubuntu
[+10.47s] DEBUG: Using session xubuntu
[+10.47s] DEBUG: Stopping greeter
[+10.47s] DEBUG: Session 1354: Sending SIGTERM
[+10.48s] DEBUG: Session 1354 exited with return value 0
[+10.48s] DEBUG: Greeter quit
[+35.51s] WARNING: Could not call SetXSession: Timeout was reached
[+60.53s] WARNING: Could not call FindUserByName: Timeout was reached
[+60.53s] DEBUG: Dropping privileges to uid 1000
[+60.54s] DEBUG: Restoring privileges
[+85.56s] WARNING: Could not call FindUserByName: Timeout was reached
[+85.56s] DEBUG: Dropping privileges to uid 1000
[+85.56s] DEBUG: Writing /home/j/.dmrc
[+85.56s] DEBUG: Restoring privileges
[+85.57s] DEBUG: Starting session xubuntu as user j
[+85.57s] DEBUG: Session 1635 running command /usr/sbin/lightdm-session startxfce4
[+85.59s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+85.59s] DEBUG: Greeter closed communication channel
```

---

### Post by pqwoerituytrueiwoq on 2012-04-27
are you using a special graphics driver?
i am not having any issues with the open-source radeon driver

---

### Post by J V on 2012-04-27
I'm using the proprietary nvidia "current-updates" driver: 295.40 on a GTX 680

I had this before with a different driver and card but it fixed itself somehow and I ignored it, but with this reinstall it's back.

---

### Post by andux on 2012-04-30
I've had same issue and found [https://bugs.launchpad.net/lightdm/+bug/870685](https://bugs.launchpad.net/lightdm/+bug/870685) .

New added users will login in time.

---

### Post by J V on 2012-04-30
Sounds like it, but mine gets past the login form: password box not greyed out, whole window dissapeared like the state in between unloading lightdm and loading xfce

However, all the other symptoms (Including the logs) are the same so I'll guess that's it.

---

### Post by Toz on 2012-04-30
Do you have accountsservice and libaccountsservice0 installed?
```
dpkg -l | grep accountsservice
ii  accountsservice                        0.6.15-2ubuntu9                         query and manipulate user account information
ii  libaccountsservice0                    0.6.15-2ubuntu9                         query and manipulate user account information - shared libraries

```

---

### Post by andux on 2012-05-01
Yes, it's installed.

After deleting the new user, delay-time comes up again.
After adding and deleting a new user the second time, my mouse sometimes doesn't react until reboot although listed in "lsusb", but there's no delay.

lightdm.log still contains two Warnings:

```

...
[+10.45s] WARNING: Could not call SetLanguage: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so language not saved
...
[+10.55s] WARNING: Could not call SetXSession: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Method "SetXSession" with signature "s" on interface "org.freedesktop.Accounts.User" doesn't exist
...

```EDIT: Cold boot shows log like first posting in thread, thus adding/deleting new users will cause only temporary effects

EDIT2: I deactivated/unchecked "PolicyKit Authentication Agent" under "Session-Settings", now even after some reboots and cold boots, there's no delay in time, but still the above written warnings.

EDIT3: Now I'm totally confused: After the fifth reboot (three cold boots in between) time-delay recurs.

EDIT4: I reinstalled nvidia-current as described in [http://ubuntuforums.org/showpost.php?p=11127302&postcount=17]("http://ubuntuforums.org/showpost.php?p=11127302&postcount=17"). Then I did several cold, warm and re-boots. Warnings are still left, but no delay in time :p

---

### Post by Toz on 2012-05-01
Have you seen this bug: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/972484]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/972484") and the two possibly related ones:
- [https://bugs.launchpad.net/lightdm/+bug/952185]("https://bugs.launchpad.net/lightdm/+bug/952185")
- [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/957431]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/957431")

Are your $HOME directories encrypted?

---

### Post by andux on 2012-05-01
It's not encrypted, but:

> **andux said:**
> 
EDIT4: I reinstalled nvidia-current as described in [http://ubuntuforums.org/showpost.php?p=11127302&postcount=17](http://ubuntuforums.org/showpost.php?p=11127302&postcount=17). Then I did several cold, warm and re-boots. Warnings are still left, but no delay in time :p


---

### Post by J V on 2012-05-01
accountsservice is isntalled

Yes my home is encrypted, it was encrypted in a previous version of ubuntu and I did a fresh install (It's on a separate partition)

Could that have caused some of the problems?

---

### Post by J V on 2012-05-01
Logging into a tty before logging into lightdm results in a perfect login, I'm guessing lightdm doesn't decrypt my data properly.

---

### Post by doob on 2012-05-01
I'm also having this issue. Home is not encrypted, I have AccountsService installed, and I've tried re-installing nvidia-current, all to no avail. This is happening on 2 different machines (both with nvidia graphics). :(

---

### Post by J V on 2012-05-01
Then something that needs to be run by the user isn't being run and lightdm chokes.

---

