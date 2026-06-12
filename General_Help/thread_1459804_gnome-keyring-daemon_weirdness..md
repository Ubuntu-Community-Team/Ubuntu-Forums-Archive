---
title: "gnome-keyring-daemon weirdness."
date: 2010-04-21
forum: General Help
---

### Post by wadam on 2010-04-21
I'm running an up-to-date installation of Lucid, and have come upon a little problem.  It seems that applications are having trouble communicating with gnome-keyring-daemon.

When I connect to wireless networks -- even ones that are in the network manager -- it always asks me for a password.

Gwibber is crashing because it can't connect to the gnome keyring daemon.

And when I open the Passwords and Encryption Keys utility (on the Accessories menu), I get the error:  "Couldn't communicate with key ring daemon."

I have verified that the daemon is starting up when I log in, that all of the appropriate keyring-related login items (certificate and key storage, secret service, & SSH key agent) are in place, and that the keyring works in other accounts on my machine.  I have tried deleting my extant keyrings, but that has produced any success.  And when I kill and restart the keyring daemon once I'm already logged in, the problem seems to abate.

I'm kind of at a loss here.  Any help?

PS -- By the way:  I don't know if it matters, but for OS X compatibility purposes, I'm running as a UID under 1000.

---

### Post by wadam on 2010-04-22
I hate to bump my own thread, but I find this problem really confounding.

Thanks.

---

### Post by vevel on 2010-04-22
I'm having similar issues, also with the updated lucid release.

I'd open a bug somewhere, but don't know where it should go.  I'll look around some more, but for now --

The keyring daemon is running, but not doing something right:
$ pgrep -fl key
5365 /usr/bin/gnome-keyring-daemon -daemonize

Killing and restarting at least fixes the issue with a few things. 
$ pkill keyring
$ /usr/bin/gnome-keyring-daemon -d
GNOME_KEYRING_CONTROL=/tmp/keyring-rcxXDQ
SSH_AUTH_SOCK=/tmp/keyring-rcxXDQ/ssh
GNOME_KEYRING_PID=14202

I'm hoping someone has more info....

---

### Post by wadam on 2010-04-22
I actually resolved my problem this afternoon.  Though perhaps not in the most painless way.  I backed up my data, deleted my account, and created a new one.  It took an hour or so to restore my settings.  
Not a method I'd recommend, but it worked in the end.

---

### Post by vevel on 2010-04-23
For reference, I've been making some progress.   I checked /var/lib/auth.log and saw issues with cracklib.  Some of the issues were resolved by redoing PAM auth:

% sudo pam-auth-update --force

Under Applications->Accessories->Passwords and Encryption Keys, I deleted all the old keys, since I was also having problems with Ubuntu One.  Those issues have now been resolved.  

I'll keep my fingers crossed that things are back to (or closer to) normal.

---

### Post by wadam on 2010-04-25
I spoke too soon when I said I resolved this.  After working for a couple of days, I'm back to not being able to connect to the gnome-keyring-daemon.  Looking at my auth.log, I seem to get the following error:  

u300 gnome-keyring-daemon[2595]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified#012Autolaunch error: X11 initialization failed.
Apr 25 17:32:59 atu300 gnome-keyring-daemon[2595]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Apr 25 17:33:00 atu300 gnome-keyring-daemon[2595]: The SSH agent was already initialized
Apr 25 17:33:00 atu300 gnome-keyring-daemon[2595]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed

Any thoughts on resolving this?

---

### Post by wadam on 2010-04-25
Alright.  I know that I'm keeping this thread single-handedly alive, however:  I figured out what is causing the problem.  When auto-login is activated on my account, I have no access to the gnome-keyring-daemon.  When auto-login is off, everything works as expected.

This, I think, suggests a serious problem for Lucid that should be taken care of before it is released.  When auto-login is activated, gwibber crashes, the Passwords and Encryption Keys application is subject to errors, I haven't tried Empathy, but I suspect that it runs into errors, and wireless passwords aren't remembered.  This is no small thing.

---

### Post by Litropy on 2010-04-26
I have the same issue. Please let me know how to get to the auth log so I, too, can paste it. Also, please tell me any other info you need to know and how to get it.

-lucid lynx NBE

---

### Post by wadam on 2010-04-27
> **Litropy said:**
> I have the same issue. Please let me know how to get to the auth log so I, too, can paste it. Also, please tell me any other info you need to know and how to get it.

-lucid lynx NBE

System>Administration>Log File Viewer.

---

### Post by darkshines87 on 2010-05-03
Hi!

I have the same issue. The keyeing daemon doesn't seem to work properly when not logging in with a password. I use fprint for logging in and I was wondering that gnome sometimes asked me for my WPA2 key and sometimes not. Now when I think about it, the keyring was not unlocked every time I successfully logged in using fprint (Every time it fails I have to type my password).

I guess the bug is as follows: If you do not log in using a password (either by frpint or by auto login) the keyring is not unlocked and also there is no automatic query to unlock it.

---

### Post by Skumpic on 2010-05-03
Same issue here  :(

When login "normally" the daemon looks like:
gnome-keyring-daemon --daemonize --login

While when autologin without a password it's looks like:
gnome-keyring-daemon --daemonize

and it's not working :(

---

### Post by Skumpic on 2010-05-03
After some googling i found out a valid solution:

[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/553032/comments/8](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/553032/comments/8)

:D

---

