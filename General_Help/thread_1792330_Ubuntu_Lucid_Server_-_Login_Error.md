---
title: "Ubuntu Lucid Server - Login Error"
date: 2011-06-28
forum: General Help
---

### Post by jazzon on 2011-06-28
I have multiple computers set up in my home (self education on networking) with one used as the main machine, and the others set up as a variety of server types.
The main machine is running Lucid, as gui based os.
The others are all running the server version.
NO Domain controller is installed, no DNS server is installed.

ALL of the server machines boot to a login prompt, allow user name and password entry, and then will fail to login with a timeout error.  After anywhere from 8-15 tries, the login will eventually succeed.

Error also occurs when logging in via ssh.

Any clues anyone?

---

### Post by Ozymandias_117 on 2011-06-28
> **jazzon said:**
> 
NO Domain controller is installed, no DNS server is installed.

ALL of the server machines boot to a login prompt, allow user name and password entry, and then will fail to login with a timeout error.  After anywhere from 8-15 tries, the login will eventually succeed.

Okay, I'm confused here, you're saying you don't have a domain controller, so all your servers should just be logging in locally, but a timeout error shouldn't occur during a local login.  So... how are you trying to login?

---

### Post by jazzon on 2011-06-28
@OZY-->
Login directly from the server terminal at boot, or from the main machine via ssh or ftp or samba depending on need.  The machines are not configured to require each others presence at boot, they each boot as independent units.  The servers are just my experiments with an http server, ftp server, samba shares etc. The primary machine (not a server) uses the full gui install of Lucid.

Basically yes, the biggest issue is the local login failure.

But no matter the method i use to login, the result is the same.  I have been working this problem for weeks now, and none of my research has turned up an explanation.

---

### Post by Ozymandias_117 on 2011-06-28
Honestly, I'm not sure, but I would start by looking in /var/log/dmesg.log as well as /var/log/auth.log to see if anything there seemed relevant.

It almost seems like the problem must be in PAM.  I can't think of anything else that would timeout...

---

### Post by jazzon on 2011-06-28
@ozy-->  I cannot find anythin wrong with the dmesg logs, auth log I am not sure of.  I am attempting to do a reboot now to get an auth log showing only local login failures.  I will post this log in a follow up in this thread.  I do not know enough about it to understand it fully, I am hoping that you ;) (or another) would be kind enough to  review it and offer more advice.

---

### Post by jazzon on 2011-06-28
auth.log file

4 failed logins occurred during the reboot which generated this auth.log.

current days login data



Jun 28 01:53:15 fort sshd[601]: Server listening on 0.0.0.0 port 22.
Jun 28 01:53:15 fort sshd[601]: Server listening on :: port 22.
Jun 28 01:53:23 fort perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Jun 28 01:53:23 fort perl: pam_winbind(webmin:auth): getting password (0x00000388)
Jun 28 01:53:23 fort perl: pam_winbind(webmin:auth): pam_get_item returned a password
Jun 28 01:54:51 fort sshd[615]: Server listening on 0.0.0.0 port 22.
Jun 28 01:54:51 fort sshd[615]: Server listening on :: port 22.
Jun 28 01:54:57 fort perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Jun 28 01:54:57 fort perl: pam_winbind(webmin:auth): getting password (0x00000388)
Jun 28 01:54:57 fort perl: pam_winbind(webmin:auth): pam_get_item returned a password
Jun 28 01:56:00 fort sshd[960]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=benden  user=EDITED_MY_USER_NAME
Jun 28 01:56:00 fort sshd[960]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 28 01:56:00 fort sshd[960]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 28 01:56:07 fort perl: pam_winbind(webmin:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'root')
Jun 28 01:56:09 fort webmin[954]: Webmin starting
Jun 28 01:56:35 fort sshd[960]: pam_winbind(sshd:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'EDITED_MY_USER_NAME')
Jun 28 01:56:38 fort sshd[960]: Failed password for EDITED_MY_USER_NAME from EDITED_MY_NETWORK_PREFIX.50 port 41533 ssh2
Jun 28 02:00:01 fort sshd[1056]: Accepted password for EDITED_MY_USER_NAME from EDITED_MY_NETWORK_PREFIX.50 port 57692 ssh2
Jun 28 02:00:01 fort sshd[1056]: pam_unix(sshd:session): session opened for user EDITED_MY_USER_NAME by (uid=0)
Jun 28 02:03:21 fort login[1284]: pam_unix(login:session): session opened for user EDITED_MY_USER_NAME by LOGIN(uid=0)
Jun 28 02:03:40 fort sudo:    EDITED_MY_USER_NAME : TTY=tty1 ; PWD=/home/EDITED_MY_USER_NAME ; USER=root ; COMMAND=/usr/bin/apt-get update
Jun 28 02:04:07 fort sudo:    EDITED_MY_USER_NAME : TTY=tty1 ; PWD=/home/EDITED_MY_USER_NAME ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Jun 28 02:04:30 fort webmin[964]: Timeout of session for EDITED_MY_USER_NAME
Jun 28 02:09:01 fort CRON[5173]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 02:09:01 fort CRON[5173]: pam_unix(cron:session): session closed for user root
|
|
Section_Removed_Non_Relevent_FTP_DATA_From_Prior_Connection
|
|
Jun 28 02:17:01 fort CRON[5328]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 02:17:01 fort CRON[5328]: pam_unix(cron:session): session closed for user root
Jun 28 02:32:43 fort login[1284]: pam_unix(login:session): session closed for user EDITED_MY_USER_NAME
Jun 28 02:39:02 fort CRON[5523]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 02:39:02 fort CRON[5523]: pam_unix(cron:session): session closed for user root
Jun 28 03:09:01 fort CRON[5801]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 03:09:01 fort CRON[5801]: pam_unix(cron:session): session closed for user root
Jun 28 03:17:01 fort CRON[5859]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 03:17:01 fort CRON[5859]: pam_unix(cron:session): session closed for user root
Jun 28 03:32:07 fort sshd[5997]: Accepted password for EDITED_MY_USER_NAME from EDITED_MY_NETWORK_PREFIX.80 port 36439 ssh2
Jun 28 03:32:07 fort sshd[5997]: pam_unix(sshd:session): session opened for user EDITED_MY_USER_NAME by (uid=0)
Jun 28 03:37:00 fort sudo:    EDITED_MY_USER_NAME : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/sbin/reboot
Jun 28 03:37:00 fort sshd[615]: Received signal 15; terminating.
Jun 28 03:37:59 fort sshd[415]: Server listening on 0.0.0.0 port 22.
Jun 28 03:37:59 fort sshd[415]: Server listening on :: port 22.
Jun 28 03:38:01 fort sshd[415]: Received signal 15; terminating.
Jun 28 03:38:01 fort sshd[663]: Server listening on 0.0.0.0 port 22.
Jun 28 03:38:01 fort sshd[663]: Server listening on :: port 22.
Jun 28 03:38:16 fort perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Jun 28 03:38:16 fort perl: pam_winbind(webmin:auth): getting password (0x00000388)
Jun 28 03:38:16 fort perl: pam_winbind(webmin:auth): pam_get_item returned a password
Jun 28 03:38:51 fort perl: pam_winbind(webmin:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'root')
Jun 28 03:38:53 fort webmin[961]: Webmin starting
Jun 28 03:39:00 fort CRON[971]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 03:39:01 fort CRON[971]: pam_unix(cron:session): session closed for user root
Jun 28 03:45:54 fort login[1102]: pam_unix(login:session): session opened for user EDITED_MY_USER_NAME by LOGIN(uid=0)

full file attached

---

### Post by jazzon on 2011-06-28
Just bumping this, still trying to get help.

---

