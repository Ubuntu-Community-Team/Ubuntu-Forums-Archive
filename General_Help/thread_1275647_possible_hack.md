---
title: "possible hack?"
date: 2009-09-26
forum: General Help
---

### Post by fcuk112 on 2009-09-26
by accident i left remote desktop setup without a password on my torrent server machine for quite a while.  when i recently accessed it to check it, i suddenly noticed someone connected via remote desktop and started running some funny commands (setting up encryption keyring).  i managed to intervene and turn off remote desktop, but i am worried that someone has already hacked the machine and installed a bot or something.  

rather than reinstalling ubuntu, is there any way i can run some checks/fixes on this box to make sure it has not been compromised?

thanks.

---

### Post by QIII on 2009-09-26
If, by "started running some funny commands" you mean that they successfully did something like actually installing an encryption keyring or anything else requiring root privileges, then you have, by definition, been compromised.

---

### Post by wojox on 2009-09-26
Where did you find the funny commands? In auth.log? Post some of them up here.

---

### Post by XCan on 2009-09-26
Post your .bash_history or the relevant parts, they may of course have deleted the relevant parts. But it's better to look in it than not.

---

### Post by Rob_H on 2009-09-26
If you're concerned about the integrity of that machine, you should reinstall. No ifs, ands, or buts.

---

### Post by Roasted on 2009-09-26
> **Rob_H said:**
> If you're concerned about the integrity of that machine, you should reinstall. No ifs, ands, or buts.

I agree.

For kicks and giggles, if I were in your shoes, I'd still like to know what happened. I'd back all of my stuff up to another drive and unmount it/disconnect it so it's out of the picture. Then spend an hour doing a little detective work. Maybe there's a log that copies ALL terminal entries?? Maybe someone here can shed light on that, but it'd sure be helpful.

Regardless - afterwards I'd reinstall. You should consider making a backup image too while you're at it. :guitar:

---

### Post by rreese6 on 2009-09-26
When anything like this happens, you will betting your knowledge against the intruder's. Since you had to ask the question, I would say the intruder has the upper hand. He could do things that your best efforts would not discover how he has setup a way to continue accessing your system.
I have run many servers. when one is compromised, like your has been, I delete the partition and reinstall. I have automatic back ups of important files and archives, I just load those back in after the system is reinstalled. Make a back-up of your personal data (basically, /home/<yourusername> but do not back up anything from the system files.

Better to be safe than sorry.

We are very curious about the "funny commands" could you post some of the information here?

---

### Post by bodhi.zazen on 2009-09-26
> **fcuk112 said:**
> by accident i left remote desktop setup without a password

VNS is the #1 problem I see on these forums. Hard to say you were "hacked" , you left the front door open is more like it.

> i suddenly noticed someone connected via remote desktop and started running some funny commands (setting up encryption keyring).  i managed to intervene and turn off remote desktop, but i am worried that someone has already hacked the machine and installed a bot or something.  

rather than reinstalling ubuntu, is there any way i can run some checks/fixes on this box to make sure it has not been compromised?

thanks.I think it is safe to assume your guest has had access to the server for quite some time. If you are interested you can image the hard drive and perform forensics at your leisure.

Disconnect your computer from the internet and re-install. Do you have other computers on your LAN that  could have been compromised ? Keep in mind this server could easily access most any box on your LAN.

This is why people put public servers in a DMZ and personally I firewall servers even on my LAN.

Best of luck and take care in the future.

/me thinks they should enforce strong password on VNC servers.

---

### Post by fcuk112 on 2009-09-26
yea, bad neglect on my part for leaving the front door open.  i first noticed it when i was logged on to the machine and suddenly the tray icon appeared to notify that someone had connected to my machine via remote desktop.  then i saw some funny commands being entered in the left-bottom side of the screen, i can't remember what the actual commands were but it had something to do with encryption keyrings.

here are the last 10 mins from auth.log:

```

Sep 27 00:30:01 bazooka dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=3840 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1236" (uid=0 pid=24379 comm="/USR/SBIN/CRON ")) 
Sep 27 00:30:02 bazooka CRON[24379]: pam_unix(cron:session): session closed for user root 
Sep 27 00:39:01 bazooka CRON[26664]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 27 00:39:01 bazooka dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=3840 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1237" (uid=0 pid=26664 comm="/USR/SBIN/CRON ")) 
Sep 27 00:39:01 bazooka CRON[26664]: pam_unix(cron:session): session closed for user root 
Sep 27 00:40:01 bazooka CRON[27024]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 27 00:40:01 bazooka dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=3840 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1238" (uid=0 pid=27024 comm="/USR/SBIN/CRON ")) 
Sep 27 00:40:01 bazooka CRON[27024]: pam_unix(cron:session): session closed for user root 

```

has the dude setup a cron session on my machine to send out messages?  can't see anything else suspicious in the file though i only glanced at it briefly.  

thanks.

---

### Post by XCan on 2009-09-26
I've yet to find any logs by Vino. Doubt you'll find anything in auth.log unless he added a user for himself, which he wouldn't be able to do without bruting your root pass.

---

### Post by fcuk112 on 2009-09-26
if it's not showing in auth.log, what kind of forensic test commands can i run?

---

### Post by DasEi on 2009-09-26
I can only follow the upper posts concerning security;

have a look at : /home/m/.bash_history  <<<shows last run cmds in bash
                 /var/log/daemon.log    <<<new or strange entries ?
                 /etc/bash.bashrc       <<<alias (sudo!) or other linking
                 /etc/sudoers           <<<new superuser ?
                 /etc/(ana)crontab      <<<new service ?

and additional install and run rkhunter/chrootkit, if you had done this before, could now check alterings

as there are too many ways for a skilled one with enough time, reinstall and care some more about securing/monitoring a system

---

### Post by fcuk112 on 2009-09-26
no i can't see anything suspicious in those files.

with rkhunter, got warnings on
/usr/sbin/unhide
/usr/sbin/unhide-linux26
(exists on the system but not present in rkhunter.dat file).

[01:19:43]   Checking if SSH root access is allowed          [ Warning ]
[01:19:43] Warning: The SSH and rkhunter configuration options should be the same:
[01:19:44]          SSH configuration option 'PermitRootLogin': yes
[01:19:44]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no

[01:19:45]   Checking /dev for suspicious file types         [ Warning ]
[01:19:45] Warning: Suspicious file types found in /dev:
[01:19:45]          /dev/shm/pulse-shm-3834670756: data

no rootkits though, and chkrootkit checks out clean.

i am not ready to repave this particular machine yet because there are some media files on there that i want to keep (and need to back up at some point).

thanks for your suggestions.

---

### Post by bodhi.zazen on 2009-09-27
I would not rely on rkhunter or chkrootkit .

Please disconnect from the internet, back up your data (you need to do this anyways), and re-install.

---

### Post by jonobe on 2009-10-26
i'm not so sure you've been hacked.

The indicator-applet is most likely the culprit - there are a lot of posts on the internet about this and it looks like a bug.  I have the problem myself and trying to eradicate it.

However, you've probably already re-installed.  But I thought i'd mention this anyway for anyone else suffering.

---

