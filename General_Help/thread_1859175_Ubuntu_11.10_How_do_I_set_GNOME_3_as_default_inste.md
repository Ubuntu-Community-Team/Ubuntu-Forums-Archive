---
title: "Ubuntu 11.10 How do I set GNOME 3 as default instead of Unity?"
date: 2011-10-13
forum: General Help
---

### Post by jonashendrickx on 2011-10-13
How do I set Gnome 3 as default instead of Unity in Oneiric? There seems to be no longer Login Screen in System Settings... So I have to change this every time I log in which is annoying. How can I set Gnome 3 or gnome-shell as default?

---

### Post by mc4man on 2011-10-13
> **jonashendrickx said:**
> So I have to change this every time I log in which is annoying. How can I set Gnome 3 or gnome-shell as default?
In a default fresh install of 11.10 the greeter will remember what session you last logged in/out of & that will be what is 'defaulted' to.

If you are doing/using  something different maybe worth mentioning

---

### Post by laine69 on 2011-10-13
yeh i have the same problem and ubuntu doesnt remember what session i was in last

---

### Post by adas on 2011-10-14
The same problem. I try to unistall unity but then X isn't started corectly :/

---

### Post by Ctrl+Alt+Del on 2011-10-14
you might wanna have a look at /var/log/lightdm/lightdm.log, i had some permission issues with my .Xauthority not being writable. You might find something in there

---

### Post by glaubersm on 2011-10-14
I want also gnome-shell as default session, but after enable automatic login, Oneiric always uses unity session. Any solution?

---

### Post by someitalian123 on 2011-10-14
Have the same problem, here's the lightdm.log

> [+0.27s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.27s] DEBUG: Starting Light Display Manager 1.0.1, UID=0 PID=1035
[+0.27s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.27s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.27s] DEBUG: Registered seat module xlocal
[+0.27s] DEBUG: Registered seat module xremote
[+0.27s] DEBUG: Adding default seat
[+0.27s] DEBUG: Starting seat
[+0.27s] DEBUG: Starting new display for automatic login as user anthony
[+0.27s] DEBUG: Starting local X display
[+0.27s] DEBUG: X server :0 will replace Plymouth
[+0.30s] DEBUG: Using VT 7
[+0.30s] DEBUG: Activating VT 7
[+0.30s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.31s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.31s] DEBUG: Launching X Server
[+0.31s] DEBUG: Launching process 1087: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.31s] DEBUG: Waiting for ready signal from X server :0
[+0.31s] DEBUG: Acquired bus name
[+0.31s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+9.16s] DEBUG: Got signal 10 from process 1087
[+9.16s] DEBUG: Got signal from X server :0
[+9.16s] DEBUG: Stopping Plymouth, X server is ready
[+9.19s] DEBUG: Connecting to XServer :0
[+9.19s] DEBUG: Automatically logging in user anthony
[+9.40s] DEBUG: pam_start("lightdm-autologin", "anthony") -> (0x93a6ce0, 0)
[+9.40s] DEBUG: pam_authenticate(0x93a6ce0, 0) -> 0 (Success)
[+9.42s] DEBUG: pam_acct_mgmt(0x93a6ce0, 0) -> 0 (Success)
[+9.42s] DEBUG: User anthony authorized
[+9.42s] DEBUG: Starting user session
[+10.03s] DEBUG: Dropping privileges to uid 1000
[+10.03s] DEBUG: Writing /home/anthony/.dmrc
[+10.05s] DEBUG: Restoring privileges
[+10.08s] DEBUG: Starting session ubuntu as user anthony logging to /home/anthony/.xsession-errors
[+10.12s] DEBUG: Launching session
[+10.12s] DEBUG: pam_set_item(0x93a6ce0, 3, ":0") -> 0 (Success)
[+10.14s] DEBUG: pam_open_session(0x93a6ce0, 0) -> 0 (Success)
[+10.35s] DEBUG: Opened ConsoleKit session 737bdc9d27f899fee679f68300000083-1318615916.867380-1306409305
[+10.35s] DEBUG: Dropping privileges to uid 1000
[+10.35s] DEBUG: Adding session authority to /home/anthony/.Xauthority
[+10.37s] DEBUG: Restoring privileges
[+10.37s] DEBUG: Launching process 1346: /usr/sbin/lightdm-session 'gnome-session --session=ubuntu'
[+10.38s] DEBUG: New display ready, switching to it
[+10.38s] DEBUG: Activating VT 7
[+10.38s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+10.41s] DEBUG: pam_setcred(0x93a6ce0, PAM_ESTABLISH_CRED) -> 0 (Success)
[+10.42s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8'
[+78.37s] DEBUG: Process 1346 exited with return value 0
[+78.37s] DEBUG: pam_close_session(0x93a6ce0) -> 0 (Success)
[+78.37s] DEBUG: pam_setcred(0x93a6ce0, PAM_DELETE_CRED) -> 0 (Success)
[+78.37s] DEBUG: pam_end(0x93a6ce0) -> 0
[+78.37s] DEBUG: Ending ConsoleKit session 737bdc9d27f899fee679f68300000083-1318615916.867380-1306409305
[+78.40s] DEBUG: User session quit
[+78.40s] DEBUG: Stopping display
[+78.40s] DEBUG: Sending signal 15 to process 1087
[+78.40s] DEBUG: Dropping privileges to uid 1000
[+78.40s] DEBUG: Removing session authority from /home/anthony/.Xauthority
[+78.41s] DEBUG: Restoring privileges
[+78.72s] DEBUG: Process 1087 exited with return value 0
[+78.72s] DEBUG: X server stopped
[+78.72s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+78.72s] DEBUG: Releasing VT 7
[+78.72s] DEBUG: Display server stopped
[+78.72s] DEBUG: Display stopped
[+78.72s] DEBUG: Active display stopped, switching to greeter
[+78.72s] DEBUG: Switching to greeter
[+78.72s] DEBUG: Starting new display for greeter
[+78.72s] DEBUG: Starting local X display
[+78.72s] DEBUG: Using VT 7
[+78.72s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+78.72s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+78.72s] DEBUG: Launching X Server
[+78.72s] DEBUG: Launching process 1818: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+78.72s] DEBUG: Waiting for ready signal from X server :0
[+79.33s] DEBUG: Got signal 10 from process 1818
[+79.33s] DEBUG: Got signal from X server :0
[+79.33s] DEBUG: Connecting to XServer :0
[+79.33s] DEBUG: Starting greeter session
[+79.34s] DEBUG: pam_start("lightdm-autologin", "lightdm") -> (0x93b4e08, 0)
[+79.34s] DEBUG: Starting session unity-greeter as user lightdm logging to /var/log/lightdm/x-0-greeter.log
[+79.36s] DEBUG: pam_authenticate(0x93b4e08, 0) -> 0 (Success)
[+79.36s] DEBUG: pam_acct_mgmt(0x93b4e08, 0) -> 0 (Success)
[+79.36s] DEBUG: Launching session
[+79.37s] DEBUG: pam_set_item(0x93b4e08, 3, ":0") -> 0 (Success)
[+79.37s] DEBUG: pam_open_session(0x93b4e08, 0) -> 0 (Success)
[+79.38s] DEBUG: Opened ConsoleKit session 737bdc9d27f899fee679f68300000083-1318615985.948767-1852897996
[+79.38s] DEBUG: Dropping privileges to uid 116
[+79.38s] DEBUG: Adding session authority to /var/lib/lightdm/.Xauthority
[+79.41s] DEBUG: Restoring privileges
[+79.41s] DEBUG: Launching process 1832: /usr/lib/lightdm/lightdm-greeter-session 'unity-greeter'
[+79.41s] WARNING: Failed to open log file /var/log/lightdm/x-0-greeter.log: Permission denied
[+79.41s] DEBUG: pam_setcred(0x93b4e08, PAM_ESTABLISH_CRED) -> 0 (Success)
[+79.41s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8'
[+79.64s] DEBUG: Read 8 bytes from greeter
[+79.64s] DEBUG: Read 9 bytes from greeter
[+79.64s] DEBUG: Greeter connected version=1.0.1
[+79.64s] DEBUG: Wrote 98 bytes to greeter
[+79.64s] DEBUG: Greeter connected, display is ready
[+79.64s] DEBUG: New display ready, switching to it
[+79.64s] DEBUG: Activating VT 7
[+79.64s] DEBUG: Stopping greeter display being switched from
[+80.22s] DEBUG: Read 8 bytes from greeter
[+80.22s] DEBUG: Read 15 bytes from greeter
[+80.23s] DEBUG: Greeter start authentication for anthony
[+80.27s] DEBUG: pam_start("lightdm", "anthony") -> (0x93bfb58, 0)
[+80.27s] DEBUG: Prompt greeter with 1 message(s)
[+80.27s] DEBUG: Wrote 45 bytes to greeter
[+93.44s] DEBUG: Read 8 bytes from greeter
[+93.44s] DEBUG: Read 13 bytes from greeter
[+93.44s] DEBUG: Continue authentication
[+93.57s] DEBUG: pam_authenticate(0x93bfb58, 0) -> 0 (Success)
[+93.57s] DEBUG: pam_acct_mgmt(0x93bfb58, 0) -> 0 (Success)
[+93.57s] DEBUG: Authenticate result for user anthony: Success
[+93.57s] DEBUG: User anthony authorized
[+93.57s] DEBUG: Wrote 27 bytes to greeter
[+93.61s] DEBUG: Read 8 bytes from greeter
[+93.61s] DEBUG: Read 15 bytes from greeter
[+93.61s] DEBUG: Greeter requests session gnome-shell
[+93.62s] DEBUG: Stopping greeter
[+93.62s] DEBUG: Dropping privileges to uid 116
[+93.62s] DEBUG: Removing session authority from /var/lib/lightdm/.Xauthority
[+93.62s] DEBUG: Restoring privileges
[+93.62s] DEBUG: Sending signal 15 to process 1832
[+93.62s] DEBUG: Process 1832 exited with return value 0
[+93.62s] DEBUG: pam_close_session(0x93b4e08) -> 0 (Success)
[+93.62s] DEBUG: pam_setcred(0x93b4e08, PAM_DELETE_CRED) -> 0 (Success)
[+93.62s] DEBUG: pam_end(0x93b4e08) -> 0
[+93.62s] DEBUG: Ending ConsoleKit session 737bdc9d27f899fee679f68300000083-1318615985.948767-1852897996
[+93.64s] DEBUG: Greeter quit
[+93.64s] DEBUG: Starting user session
[+93.68s] DEBUG: Dropping privileges to uid 1000
[+93.68s] DEBUG: Writing /home/anthony/.dmrc
[+93.68s] DEBUG: Restoring privileges
[+93.68s] DEBUG: Starting session gnome-shell as user anthony logging to /home/anthony/.xsession-errors
[+93.68s] DEBUG: Launching session
[+93.68s] DEBUG: pam_set_item(0x93bfb58, 3, ":0") -> 0 (Success)
[+93.69s] DEBUG: pam_open_session(0x93bfb58, 0) -> 0 (Success)
[+93.70s] DEBUG: Opened ConsoleKit session 737bdc9d27f899fee679f68300000083-1318616000.268741-307897395
[+93.70s] DEBUG: Dropping privileges to uid 1000
[+93.70s] DEBUG: Adding session authority to /home/anthony/.Xauthority
[+93.71s] DEBUG: Restoring privileges
[+93.71s] DEBUG: Launching process 1927: /usr/sbin/lightdm-session 'gnome-session --session=gnome'
[+93.71s] DEBUG: pam_setcred(0x93bfb58, PAM_ESTABLISH_CRED) -> 0 (Success)
[+93.71s] DEBUG: PAM returns environment 'GNOME_KEYRING_CONTROL=/tmp/keyring-HhQOau GNOME_KEYRING_PID=1917 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8'
[+93.71s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1

---

### Post by laine69 on 2011-10-14
found it:
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell


source: [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by glaubersm on 2011-10-14
> **laine69 said:**
> found it:
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell


source: [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Solved here!
Thank you very much, friend.

---

### Post by softwareregisterac on 2011-10-17
This was awesome !!!
Been to five different sites to solve this ..... I don't Unity one bit .....
You make my day!!!

---

### Post by softwareregisterac on 2011-10-17
Originally Posted by **laine69** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11343268#post11343268") 				
 				found it:
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell


This was awesome !!!
Been to five different sites to solve this ..... I don't Unity one bit .....
You make my day!!!

---

