---
title: "Authentication service cannot retrieve authentication info"
date: 2012-03-09
forum: General Help
---

### Post by kikotiger on 2012-03-09
I recently updated my system (Ubuntu 10.04) and I noticed there was a kernel update to 2.6.32-39. After I rebooted to apply the update I tried to login and after I enter my password an error message appeared saying "Authentication service cannot retrieve authentication info." 
I tried logging in from tty and it would say "Incorrect Login." I have already tried to make my account login automatically but I get an error saying "Permission denied." I also added a new user and tried to login with the new account and it also says "Permission denied." 
Any help or suggestions? I am able to login from safe mode but only as root and I hadn't edited any files.

---

### Post by matt_symes on 2012-03-09
Hi

Is this a problem with the file /etc/shadow ?

What are the permissions on it ?

```
ls -l /etc/shadow
```

What about your user ? From a root console...

```
grep -i <user_name> /etc/shadow
```

Can you su to it ? From the root console

```
su - <user_name>
```

Change <user_name> to your user name

Kind regards

---

### Post by kikotiger on 2012-03-09
I don't think is the shadow file, here is the output of the commands:

root@mobile-3:~# ls -l /etc/shadow
-r--r----- 1 root shadow 1352 2011-12-09 10:03 /etc/shadow
root@mobile-3:~# grep -i kiko /etc/shadow
kiko:$6$AgrXYo3H$spriR/4ASDlUZsq/dKZGKkty6g0JJB/XCpCLsu2uNVgIPupf30UC11.zwFc1K27T1D6MjA3rAWeTz2WammnGg/:15408:0:99999:7:::
root@mobile-3:~# su - kiko
kiko@mobile-3:~$ 

I had previously run pwconv and pwunconv to try to fix the problem but it didn't do anything. Except that it removed the shadow file, I used the pwconv command again and it created the shadow file again. Then I noticed there was a shadow- file and run the second command and got this:

root@mobile-3:/etc# grep -i kiko /etc/shadow-
kiko:$6$gy0HzPZE$KS5Oxm.MT8Vrnkfj7DXlTV0Wn2xnWJLvSuvMGU3Dx9L2Xx2N3dX2RFDvJ9GehDcHWJVejWFN0ai/KE2lMd20q0:15315:0:99999:7:::
root@mobile-3:/etc# grep -i kiko /etc/shadow
kiko:$6$AgrXYo3H$spriR/4ASDlUZsq/dKZGKkty6g0JJB/XCpCLsu2uNVgIPupf30UC11.zwFc1K27T1D6MjA3rAWeTz2WammnGg/:15408:0:99999:7:::

Not sure if this helps. I'm still unable to login after creating the shadow file.

---

### Post by matt_symes on 2012-03-09
Hi

These are the default permissions for shadow

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/shadow
-rw-r----- 1 root shadow 1103 Mar  6 18:04 /etc/shadow
matthew@matthew-Aspire-7540:~$ 
```

From a root console.

```
chmod 640 /etc/shadow
```

Give that a try.

Kind regards

---

### Post by kikotiger on 2012-03-09
I changed the permission on the shadow file but I'm still unable to login. I have already search for similar problems and most point to LDAP, which I don't think I use. Do you have any other advice?
Thanks.

---

### Post by matt_symes on 2012-03-09
Hi

Is the problem with PAM ?

```
ls -l /etc/pam.d/
```

The file /etc/passwd is configured correctly ?

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/passwd
-rw-r--r-- 1 root root 1791 Mar  6 18:04 /etc/passwd
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by kikotiger on 2012-03-09
I'm not sure if is pam, this is the output of the commands:
```
root@mobile-3:~# ls -l /etc/pam.d/
total 96
-rw-r--r-- 1 root root  182 2009-08-14 11:49 atd
-rw-r--r-- 1 root root  384 2010-01-26 11:01 chfn
-rw-r--r-- 1 root root   92 2010-01-26 11:01 chpasswd
-rw-r--r-- 1 root root  581 2010-01-26 11:01 chsh
-rw-r--r-- 1 root root 1208 2012-03-05 19:05 common-account
-rw-r--r-- 1 root root 1287 2012-03-05 19:05 common-auth
-rw-r--r-- 1 root root 1480 2012-03-05 19:05 common-password
-rw-r--r-- 1 root root 1201 2012-03-05 19:05 common-session
-rw-r--r-- 1 root root 1154 2012-03-05 19:05 common-session-noninteractive
-rw-r--r-- 1 root root  307 2010-04-15 01:51 cron
-rw-r--r-- 1 root root   69 2010-11-02 12:55 cups
-rw-r--r-- 1 root root  267 2008-11-10 17:32 cvs
-rw-r--r-- 1 root root  648 2011-04-28 03:08 gdm
-rw-r--r-- 1 root root  495 2011-04-28 03:08 gdm-autologin
-rw-r--r-- 1 root root   56 2011-03-08 02:29 gnome-screensaver
-rw-r--r-- 1 root root 3967 2010-01-26 11:01 login
-rw-r--r-- 1 root root   92 2010-01-26 11:01 newusers
-rw-r--r-- 1 root root  520 2010-04-13 17:01 other
-rw-r--r-- 1 root root   92 2010-01-26 11:01 passwd
-rw-r--r-- 1 root root  105 2011-04-19 16:05 polkit-1
-rw-r--r-- 1 root root  168 2010-03-06 23:36 ppp
-rw-r--r-- 1 root root   84 2010-03-19 16:16 samba
-rw-r--r-- 1 root root 2305 2010-01-26 11:01 su
-rw-r--r-- 1 root root  119 2010-04-13 12:37 sudo
root@mobile-3:~# ls -l /etc/passwd
-rw-r--r-- 1 root root 2041 2012-03-09 13:16 /etc/passwd

```

Thanks

---

### Post by matt_symes on 2012-03-09
Hi

The file permissions look fine. What's the output of this file

```
cat /etc/pam.d/login
```

Kind regards

---

### Post by kikotiger on 2012-03-09
This is what the login file contain:
```

root@mobile-3:~# cat /etc/pam.d/login
#
# The PAM configuration file for the Shadow `login' service
#

# Enforce a minimal delay in case of failure (in microseconds).
# (Replaces the `FAIL_DELAY' setting from login.defs)
# Note that other modules may require another minimal delay. (for example,
# to disable any delay, you should add the nodelay option to pam_unix)
auth       optional   pam_faildelay.so  delay=3000000

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
# Note that it is included as a "required" module. root will be
# prompted for a password on insecure ttys.
# If you change it to a "requisite" module, make sure this does not leak
# user name information.
auth       required  pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

# SELinux needs to be the first session rule. This ensures that any 
# lingering context has been cleared. Without out this it is possible 
# that a module could execute code in the wrong domain.
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# This allows certain extra groups to be granted to a user
# based on things like time of day, tty, service, and user.
# Please edit /etc/security/group.conf to fit your needs
# (Replaces the `CONSOLE_GROUPS' option in login.defs)
auth       optional   pam_group.so

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on logins.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# Uncomment and edit /etc/security/access.conf if you need to
# set access limits.
# (Replaces /etc/login.access file)
# account  required       pam_access.so

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

# Prints the last login info upon succesful login
# (Replaces the `LASTLOG_ENAB' option from login.defs)
session    optional   pam_lastlog.so

# Prints the motd upon succesful login
# (Replaces the `MOTD_FILE' option in login.defs)
session    optional   pam_motd.so

# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). 
#
# This also defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
session    optional   pam_mail.so standard

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password

# SELinux needs to intervene at login time to ensure that the process
# starts in the proper default security context. Only sessions which are
# intended to run in the user's context should be run after this.
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
# When the module is present, "required" would be sufficient (When SELinux
# is disabled, this returns success.)

```

Thanks

---

### Post by matt_symes on 2012-03-09
Hi

That file looks alright. 

You have me scratching my head here. Anybody else with ideas ?

Anything on the log files /var/log/auth.log ?

Kind regards

---

### Post by kikotiger on 2012-03-09
I appreciate your help, I don't feel safe using the root account as my everyday account. I will give it some time maybe some one else can give any suggestion, otherwise I might have to reinstall.
Thanks for your help and any mode advices are welcome.

---

### Post by matt_symes on 2012-03-09
Hi

You may have missed this.

> Anything in the log files /var/log/auth.log  or syslog ?

Kind regards

---

### Post by kikotiger on 2012-03-09
This is what I found from two auth.log files
```

Mar  4 00:17:01 mobile-3 CRON[7460]: pam_unix(cron:session): session closed for user root
Mar  5 17:26:20 mobile-3 gdm-session-worker[1746]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 17:26:24 mobile-3 gdm-session-worker[1746]: pam_unix(gdm:session): session opened for user kiko by (uid=0)
Mar  5 17:26:24 mobile-3 gdm-session-worker[1746]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar  5 17:26:25 mobile-3 polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Mar  5 17:39:02 mobile-3 CRON[2308]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  5 17:39:02 mobile-3 CRON[2308]: pam_unix(cron:session): session closed for user root
Mar  5 18:09:01 mobile-3 CRON[2684]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  5 18:09:01 mobile-3 CRON[2684]: pam_unix(cron:session): session closed for user root
Mar  5 18:17:01 mobile-3 CRON[2691]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  5 18:17:01 mobile-3 CRON[2691]: pam_unix(cron:session): session closed for user root
Mar  5 18:39:01 mobile-3 CRON[2743]: pam_unix(cron:session): session opened for user root by (uid=0)
[B]Mar  5 18:39:01 mobile-3 CRON[2743]: pam_unix(cron:session): session closed for user root
Mar  5 19:01:04 mobile-3 sudo:     kiko : TTY=unknown ; PWD=/home/kiko ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 79691813 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpBP0NXu
Mar  5 19:07:33 mobile-3 login[1148]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:07:33 mobile-3 login[1148]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:07:42 mobile-3 login[1148]: FAILED LOGIN (1) on '/dev/tty2' FOR 'kiko', Authentication service cannot retrieve authentication info[/B]
Mar  5 19:07:58 mobile-3 login[1148]: FAILED LOGIN (2) on '/dev/tty2' FOR 'kiko', Authentication service cannot retrieve authentication info
Mar  5 19:08:24 mobile-3 login[1662]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:08:24 mobile-3 login[1662]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:08:30 mobile-3 login[1662]: FAILED LOGIN (1) on '/dev/tty1' FOR 'kiko', Authentication service cannot retrieve authentication info
Mar  5 19:08:40 mobile-3 login[1662]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=root
Mar  5 19:08:43 mobile-3 login[1662]: FAILED LOGIN (2) on '/dev/tty1' FOR 'root', User not known to the underlying authentication module
Mar  5 19:15:59 mobile-3 polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.12 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar  5 19:18:58 mobile-3 gdm-session-worker[1700]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:18:58 mobile-3 gdm-session-worker[1700]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:18:58 mobile-3 gdm-session-worker[1700]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 19:19:09 mobile-3 gdm-session-worker[1819]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:19:09 mobile-3 gdm-session-worker[1819]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:19:09 mobile-3 gdm-session-worker[1819]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 19:19:22 mobile-3 gdm-session-worker[1828]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:19:22 mobile-3 gdm-session-worker[1828]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 19:19:22 mobile-3 gdm-session-worker[1828]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 19:19:26 mobile-3 gdm-session-worker[1828]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:27:06 mobile-3 gdm-session-worker[1717]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:06 mobile-3 gdm-session-worker[1717]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:06 mobile-3 gdm-session-worker[1717]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:27:16 mobile-3 gdm-session-worker[1836]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:16 mobile-3 gdm-session-worker[1836]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:16 mobile-3 gdm-session-worker[1836]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:27:19 mobile-3 gdm-session-worker[1836]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:27:39 mobile-3 gdm-session-worker[1845]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:39 mobile-3 gdm-session-worker[1845]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:39 mobile-3 gdm-session-worker[1845]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:27:43 mobile-3 gdm-session-worker[1845]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:27:51 mobile-3 gdm-session-worker[1854]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:51 mobile-3 gdm-session-worker[1854]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:27:51 mobile-3 gdm-session-worker[1854]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:27:53 mobile-3 gdm-session-worker[1854]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:28:02 mobile-3 gdm-session-worker[1863]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:02 mobile-3 gdm-session-worker[1863]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:02 mobile-3 gdm-session-worker[1863]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:28:10 mobile-3 gdm-session-worker[1863]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:28:18 mobile-3 gdm-session-worker[1872]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:18 mobile-3 gdm-session-worker[1872]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:18 mobile-3 gdm-session-worker[1872]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:28:26 mobile-3 gdm-session-worker[1872]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kiko
Mar  5 20:28:40 mobile-3 gdm-session-worker[1881]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:40 mobile-3 gdm-session-worker[1881]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:40 mobile-3 gdm-session-worker[1881]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kiko"
Mar  5 20:28:53 mobile-3 gdm-session-worker[1890]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:53 mobile-3 gdm-session-worker[1890]: PAM pam_parse: expecting return value; [...sucess=2 default=ignore]
Mar  5 20:28:55 mobile-3 gdm-session-worker[1890]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "root"
Mar  5 20:28:59 mobile-3 gdm-session-worker[1890]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=root

```

And this is from the syslog:
```

Mar  5 18:09:01 mobile-3 CRON[2686]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Mar  5 18:17:01 mobile-3 CRON[2693]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  5 18:39:01 mobile-3 CRON[2745]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Mar  5 18:53:10 mobile-3 wpa_supplicant[1272]: WPA: Group rekeying completed with 00:1e:e5:83:71:28 [GTK=TKIP]
Mar  5 18:53:10 mobile-3 NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Mar  5 18:53:10 mobile-3 NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Mar  5 19:00:59 mobile-3 kernel: [ 5781.547769] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input18
Mar  5 19:02:57 mobile-3 dbus-daemon: Reloaded configuration
Mar  5 19:03:34 mobile-3 kernel: [ 5937.295814] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar  5 19:03:34 mobile-3 kernel: [ 5937.297059] SGI XFS Quota Management subsystem
Mar  5 19:03:34 mobile-3 kernel: [ 5937.342672] JFS: nTxBlock = 8192, nTxLock = 65536
Mar  5 19:03:34 mobile-3 kernel: [ 5937.402391] NTFS driver 2.1.29 [Flags: R/O MODULE].
Mar  5 19:03:34 mobile-3 kernel: [ 5937.467738] QNX4 filesystem 0.2.3 registered.
Mar  5 19:03:35 mobile-3 kernel: [ 5937.584857] Btrfs loaded
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Version 2010.3.6 external FUSE 28
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Mounted /dev/sda2 (Read-Only, label "Win7", NTFS 3.1)
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Cmdline options: ro
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Mount options: ro,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Ownership and permissions disabled, configuration type 1
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: mounted as ntfs-3g filesystem
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Mar  5 19:03:35 mobile-3 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Mar  5 19:03:35 mobile-3 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Mar  5 19:03:35 mobile-3 macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Mar  5 19:03:35 mobile-3 20microsoft: debug: /dev/sda2 is a NTFS partition
Mar  5 19:03:35 mobile-3 20microsoft: result: /dev/sda2:Windows 7 (loader):Windows:chain
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Mar  5 19:03:35 mobile-3 ntfs-3g[7253]: Unmounting /dev/sda2 (Win7)
Mar  5 19:03:35 mobile-3 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 macosx-prober: debug: /dev/sda3 is not an HFS+ partition: exiting
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 20microsoft: debug: /dev/sda3 is a FUSE partition
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 30utility: debug: /dev/sda3 is not a FAT partition: exiting
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda3
Mar  5 19:03:35 mobile-3 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda4
Mar  5 19:03:35 mobile-3 50mounted-tests: debug: /dev/sda4 is a swap partition; skipping
Mar  5 19:03:35 mobile-3 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Mar  5 19:03:36 mobile-3 dkms_autoinstaller: bcmwl (5.60.48.36+bdcom): Installing module on kernel 2.6.32-39-generic.
Mar  5 19:03:58 mobile-3 dkms_autoinstaller: vboxhost (4.1.8): Installing module on kernel 2.6.32-39-generic.
Mar  5 19:04:42 mobile-3 dbus-daemon: Reloaded configuration
Mar  5 19:05:18 mobile-3 AptDaemon: INFO: Initializing daemon
Mar  5 19:06:58 mobile-3 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar  5 19:06:58 mobile-3 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1026" x-info="http://www.rsyslog.com"] (re)start
Mar  5 19:06:58 mobile-3 rsyslogd: rsyslogd's groupid changed to 103
Mar  5 19:06:58 mobile-3 rsyslogd: rsyslogd's userid changed to 101
Mar  5 19:06:58 mobile-3 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Initializing cgroup subsys cpu
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Linux version 2.6.32-39-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #86-Ubuntu SMP Mon Feb 13 21:50:08 UTC 2012 (Ubuntu 2.6.32-39.86-generic 2.6.32.56+drm33.22)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-39-generic root=UUID=9a21ba86-2a24-4849-bcfe-ad32df96d2e5 ro quiet splash
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] KERNEL supported cpus:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   Intel GenuineIntel
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   AMD AuthenticAMD
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   Centaur CentaurHauls
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] BIOS-provided physical RAM map:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe72000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000dfe72000 - 00000000e0000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] DMI 2.4 present.
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] MTRR default type: uncachable
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] MTRR fixed ranges enabled:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   00000-9FFFF write-back
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   A0000-BFFFF uncachable
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   C0000-CFFFF write-protect
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   D0000-EFFFF uncachable
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   F0000-FFFFF write-protect
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] MTRR variable ranges enabled:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   2 base 0C0000000 mask FE0000000 write-back
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   3 base 100000000 mask FE0000000 write-back
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   4 base 0DFF00000 mask FFFF00000 uncachable
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   5 disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   6 disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   7 disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] last_pfn = 0xdfe72 max_arch_pfn = 0x400000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] modified physical RAM map:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfe72000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000dfe72000 - 00000000e0000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] initial memory mapped : 0 - 20000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dfe72000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] NX (Execute Disable) protection: active
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  0000000000 - 00dfe00000 page 2M
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  00dfe00000 - 00dfe72000 page 4k
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] kernel direct mapping tables up to dfe72000 @ 8000-e000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] NX (Execute Disable) protection: active
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  0100000000 - 0120000000 page 2M
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] RAMDISK: 377f4000 - 37fef008
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: RSDP 00000000000fbc90 00024 (v02 DELL  )
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: XSDT 00000000dfe73a00 00064 (v01 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: FACP 00000000dfe7389c 000F4 (v04 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: DSDT 00000000dfe74000 04BC2 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: FACS 00000000dfe82800 00040
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: HPET 00000000dfe73b00 00038 (v01 DELL    M08     00000001 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: APIC 00000000dfe73c00 00068 (v01 DELL    M08     27D80B13 ASL  00000047)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: MCFG 00000000dfe73bc0 0003E (v16 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: SLIC 00000000dfe73c9c 00176 (v01 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: OSFR 00000000dfe73200 0002C (v01 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: BOOT 00000000dfe737c0 00028 (v01 DELL    M08     27D80B13 ASL  00000061)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: SSDT 00000000dfe7217e 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] No NUMA configuration found
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   bootmap [0000000000012000 -  0000000000035fff] pages 24
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #2 [0001000000 - 0001a35ac4]    TEXT DATA BSS ==> [0001000000 - 0001a35ac4]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #3 [00377f4000 - 0037fef008]          RAMDISK ==> [00377f4000 - 0037fef008]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #5 [0001a36000 - 0001a361ec]              BRK ==> [0001a36000 - 0001a361ec]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Zone PFN ranges:
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Movable zone start PFN for each node
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] early_node_map[4] active PFN ranges
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]     0: 0x00000100 -> 0x000dfe72
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] On node 0 totalpages: 1048076
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA zone: 105 pages reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA zone: 3833 pages, LIFO batch:0
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   DMA32 zone: 898730 pages, LIFO batch:31
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   Normal zone: 1792 pages used for memmap
Mar  5 19:06:58 mobile-3 kernel: [    0.000000]   Normal zone: 129280 pages, LIFO batch:31
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] nr_irqs_gsi: 24
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000dfe72000 - 00000000e0000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe00000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u1048576
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] pcpu-alloc: s91608 r8192 d23080 u1048576 alloc=1*2097152
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031843
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Policy zone: Normal
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-39-generic root=UUID=9a21ba86-2a24-4849-bcfe-ad32df96d2e5 ro quiet splash
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Initializing CPU#0
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Checking aperture...
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] No AGP bridge found
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Memory: 4047836k/4718592k available (5437k kernel code, 526288k absent, 144468k reserved, 2981k data, 884k init)
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Hierarchical RCU implementation.
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Extended CMOS year: 2000
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Console: colour VGA+ 80x25
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] console [tty0] enabled
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] hpet clockevent registered
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Fast TSC calibration using PIT
Mar  5 19:06:58 mobile-3 kernel: [    0.000000] Detected 2493.542 MHz processor.
Mar  5 19:06:58 mobile-3 kernel: [    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4987.08 BogoMIPS (lpj=24935420)
Mar  5 19:06:58 mobile-3 kernel: [    0.010034] Security Framework initialized
Mar  5 19:06:58 mobile-3 kernel: [    0.010055] AppArmor: AppArmor initialized
Mar  5 19:06:58 mobile-3 kernel: [    0.010382] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.012866] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.014029] Mount-cache hash table entries: 256
Mar  5 19:06:58 mobile-3 kernel: [    0.014183] Initializing cgroup subsys ns
Mar  5 19:06:58 mobile-3 kernel: [    0.014188] Initializing cgroup subsys cpuacct
Mar  5 19:06:58 mobile-3 kernel: [    0.014191] Initializing cgroup subsys memory
Mar  5 19:06:58 mobile-3 kernel: [    0.014199] Initializing cgroup subsys devices
Mar  5 19:06:58 mobile-3 kernel: [    0.014201] Initializing cgroup subsys freezer
Mar  5 19:06:58 mobile-3 kernel: [    0.014203] Initializing cgroup subsys net_cls
Mar  5 19:06:58 mobile-3 kernel: [    0.014225] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 19:06:58 mobile-3 kernel: [    0.014227] CPU: L2 cache: 6144K
Mar  5 19:06:58 mobile-3 kernel: [    0.014231] CPU 0/0x0 -> Node 0
Mar  5 19:06:58 mobile-3 kernel: [    0.014233] CPU: Physical Processor ID: 0
Mar  5 19:06:58 mobile-3 kernel: [    0.014234] CPU: Processor Core ID: 0
Mar  5 19:06:58 mobile-3 kernel: [    0.014237] mce: CPU supports 6 MCE banks
Mar  5 19:06:58 mobile-3 kernel: [    0.014246] CPU0: Thermal monitoring enabled (TM2)
Mar  5 19:06:58 mobile-3 kernel: [    0.014250] using mwait in idle threads.
Mar  5 19:06:58 mobile-3 kernel: [    0.014252] Performance Events: Core2 events, Intel PMU driver.
Mar  5 19:06:58 mobile-3 kernel: [    0.014258] ... version:                2
Mar  5 19:06:58 mobile-3 kernel: [    0.014259] ... bit width:              40
Mar  5 19:06:58 mobile-3 kernel: [    0.014261] ... generic registers:      2
Mar  5 19:06:58 mobile-3 kernel: [    0.014262] ... value mask:             000000ffffffffff
Mar  5 19:06:58 mobile-3 kernel: [    0.014263] ... max period:             000000007fffffff
Mar  5 19:06:58 mobile-3 kernel: [    0.014265] ... fixed-purpose events:   3
Mar  5 19:06:58 mobile-3 kernel: [    0.014266] ... event mask:             0000000700000003
Mar  5 19:06:58 mobile-3 kernel: [    0.020027] ACPI: Core revision 20090903
Mar  5 19:06:58 mobile-3 kernel: [    0.030008] ftrace: converting mcount calls to 0f 1f 44 00 00
Mar  5 19:06:58 mobile-3 kernel: [    0.030014] ftrace: allocating 22574 entries in 89 pages
Mar  5 19:06:58 mobile-3 kernel: [    0.038515] Setting APIC routing to flat
Mar  5 19:06:58 mobile-3 kernel: [    0.038890] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar  5 19:06:58 mobile-3 kernel: [    0.139621] CPU0: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
Mar  5 19:06:58 mobile-3 kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] Initializing CPU#1
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU: L2 cache: 6144K
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU 1/0x1 -> Node 0
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU: Physical Processor ID: 0
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU: Processor Core ID: 1
Mar  5 19:06:58 mobile-3 kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Mar  5 19:06:58 mobile-3 kernel: [    0.290054] CPU1: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
Mar  5 19:06:58 mobile-3 kernel: [    0.290061] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar  5 19:06:58 mobile-3 kernel: [    0.300024] Brought up 2 CPUs
Mar  5 19:06:58 mobile-3 kernel: [    0.300027] Total of 2 processors activated (9974.56 BogoMIPS).
Mar  5 19:06:58 mobile-3 kernel: [    0.301735] CPU0 attaching sched-domain:
Mar  5 19:06:58 mobile-3 kernel: [    0.301739]  domain 0: span 0-1 level MC
Mar  5 19:06:58 mobile-3 kernel: [    0.301741]   groups: 0 1
Mar  5 19:06:58 mobile-3 kernel: [    0.301745] CPU1 attaching sched-domain:
Mar  5 19:06:58 mobile-3 kernel: [    0.301747]  domain 0: span 0-1 level MC
Mar  5 19:06:58 mobile-3 kernel: [    0.301749]   groups: 1 0
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] devtmpfs: initialized
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] regulator: core version 0.5
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] Time: 19:06:43  Date: 03/05/12
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] NET: Registered protocol family 16
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] Trying to unpack rootfs image as initramfs...
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] ACPI: bus type pci registered
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Mar  5 19:06:58 mobile-3 kernel: [    0.301806] PCI: MCFG area at f8000000 reserved in E820
Mar  5 19:06:58 mobile-3 kernel: [    0.301908] PCI: Using MMCONFIG at f8000000 - fbffffff
Mar  5 19:06:58 mobile-3 kernel: [    0.301910] PCI: Using configuration type 1 for base access
Mar  5 19:06:58 mobile-3 kernel: [    0.310055] bio: create slab <bio-0> at 0
Mar  5 19:06:58 mobile-3 kernel: [    0.310654] ACPI: EC: Look up EC in DSDT
Mar  5 19:06:58 mobile-3 kernel: [    0.329339] ACPI: Interpreter enabled
Mar  5 19:06:58 mobile-3 kernel: [    0.329342] ACPI: (supports S0 S3 S4 S5)
Mar  5 19:06:58 mobile-3 kernel: [    0.329358] ACPI: Using IOAPIC for interrupt routing
Mar  5 19:06:58 mobile-3 kernel: [    0.367459] ACPI: No dock devices found.
Mar  5 19:06:58 mobile-3 kernel: [    0.381297] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar  5 19:06:58 mobile-3 kernel: [    0.381423] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.381427] pci 0000:00:01.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.381513] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
Mar  5 19:06:58 mobile-3 kernel: [    0.381582] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
Mar  5 19:06:58 mobile-3 kernel: [    0.381657] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.381737] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.381742] pci 0000:00:1a.7: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.381799] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6ffc000-0xf6ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.381883] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.381887] pci 0000:00:1b.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.382006] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.382010] pci 0000:00:1c.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.382133] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.382137] pci 0000:00:1c.1: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.382261] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.382266] pci 0000:00:1c.4: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.382332] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
Mar  5 19:06:58 mobile-3 kernel: [    0.382401] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
Mar  5 19:06:58 mobile-3 kernel: [    0.382471] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
Mar  5 19:06:58 mobile-3 kernel: [    0.382544] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.382626] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.382631] pci 0000:00:1d.7: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.382823] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Mar  5 19:06:58 mobile-3 kernel: [    0.382829] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
Mar  5 19:06:58 mobile-3 kernel: [    0.382833] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Mar  5 19:06:58 mobile-3 kernel: [    0.382837] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 006c (mask 0007)
Mar  5 19:06:58 mobile-3 kernel: [    0.382841] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Mar  5 19:06:58 mobile-3 kernel: [    0.382912] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
Mar  5 19:06:58 mobile-3 kernel: [    0.382919] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
Mar  5 19:06:58 mobile-3 kernel: [    0.382927] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
Mar  5 19:06:58 mobile-3 kernel: [    0.382934] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
Mar  5 19:06:58 mobile-3 kernel: [    0.382941] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
Mar  5 19:06:58 mobile-3 kernel: [    0.383018] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
Mar  5 19:06:58 mobile-3 kernel: [    0.383026] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
Mar  5 19:06:58 mobile-3 kernel: [    0.383034] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
Mar  5 19:06:58 mobile-3 kernel: [    0.383041] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
Mar  5 19:06:58 mobile-3 kernel: [    0.383049] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383056] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf6ffb800-0xf6ffbfff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383117] pci 0000:00:1f.2: PME# supported from D3hot
Mar  5 19:06:58 mobile-3 kernel: [    0.383122] pci 0000:00:1f.2: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.383155] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6ffb700-0xf6ffb7ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383179] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
Mar  5 19:06:58 mobile-3 kernel: [    0.383263] pci 0000:01:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383278] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383294] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf2000000-0xf3ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383302] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
Mar  5 19:06:58 mobile-3 kernel: [    0.383311] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383444] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383447] pci 0000:00:01.0: bridge 32bit mmio: [0xf2000000-0xf6efffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383451] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383531] pci 0000:09:00.0: reg 10 64bit mmio: [0xf1ffc000-0xf1ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383542] pci 0000:09:00.0: reg 18 io port: [0xde00-0xdeff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383666] pci 0000:09:00.0: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.383668] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.383674] pci 0000:09:00.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.383752] pci 0000:00:1c.0: bridge io port: [0xd000-0xdfff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383757] pci 0000:00:1c.0: bridge 32bit mmio: [0xf1f00000-0xf1ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.383968] pci 0000:0b:00.0: reg 10 64bit mmio: [0xf1efc000-0xf1efffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384280] pci 0000:0b:00.0: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.384281] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.384293] pci 0000:0b:00.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.384433] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1e00000-0xf1efffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384498] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384502] pci 0000:00:1c.4: bridge 32bit mmio: [0xf1c00000-0xf1dfffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384510] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384574] pci 0000:03:09.0: reg 10 32bit mmio: [0xf1bff800-0xf1bfffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384646] pci 0000:03:09.0: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.384647] pci 0000:03:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.384652] pci 0000:03:09.0: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.384698] pci 0000:03:09.1: reg 10 32bit mmio: [0xf1bff500-0xf1bff5ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384770] pci 0000:03:09.1: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.384772] pci 0000:03:09.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.384776] pci 0000:03:09.1: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.384818] pci 0000:03:09.2: reg 10 32bit mmio: [0xf1bff600-0xf1bff6ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.384890] pci 0000:03:09.2: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.384892] pci 0000:03:09.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.384897] pci 0000:03:09.2: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.384943] pci 0000:03:09.3: reg 10 32bit mmio: [0xf1bff700-0xf1bff7ff]
Mar  5 19:06:58 mobile-3 kernel: [    0.385015] pci 0000:03:09.3: supports D1 D2
Mar  5 19:06:58 mobile-3 kernel: [    0.385016] pci 0000:03:09.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 19:06:58 mobile-3 kernel: [    0.385021] pci 0000:03:09.3: PME# disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.385077] pci 0000:00:1e.0: transparent bridge
Mar  5 19:06:58 mobile-3 kernel: [    0.385084] pci 0000:00:1e.0: bridge 32bit mmio: [0xf1b00000-0xf1bfffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.385122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.385342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.385443] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.385490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.385547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.385609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Mar  5 19:06:58 mobile-3 kernel: [    0.395466] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Mar  5 19:06:58 mobile-3 kernel: [    0.395565] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Mar  5 19:06:58 mobile-3 kernel: [    0.395662] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
Mar  5 19:06:58 mobile-3 kernel: [    0.395748] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Mar  5 19:06:58 mobile-3 kernel: [    0.395847] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar  5 19:06:58 mobile-3 kernel: [    0.395946] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar  5 19:06:58 mobile-3 kernel: [    0.396047] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar  5 19:06:58 mobile-3 kernel: [    0.396134] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar  5 19:06:58 mobile-3 kernel: [    0.396256] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Mar  5 19:06:58 mobile-3 kernel: [    0.396261] vgaarb: loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.396369] SCSI subsystem initialized
Mar  5 19:06:58 mobile-3 kernel: [    0.396466] libata version 3.00 loaded.
Mar  5 19:06:58 mobile-3 kernel: [    0.396560] usbcore: registered new interface driver usbfs
Mar  5 19:06:58 mobile-3 kernel: [    0.396560] usbcore: registered new interface driver hub
Mar  5 19:06:58 mobile-3 kernel: [    0.396573] usbcore: registered new device driver usb
Mar  5 19:06:58 mobile-3 kernel: [    0.396700] ACPI: WMI: Mapper loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.396702] PCI: Using ACPI for IRQ routing
Mar  5 19:06:58 mobile-3 kernel: [    0.396964] NetLabel: Initializing
Mar  5 19:06:58 mobile-3 kernel: [    0.396966] NetLabel:  domain hash size = 128
Mar  5 19:06:58 mobile-3 kernel: [    0.396967] NetLabel:  protocols = UNLABELED CIPSOv4
Mar  5 19:06:58 mobile-3 kernel: [    0.396981] NetLabel:  unlabeled traffic allowed by default
Mar  5 19:06:58 mobile-3 kernel: [    0.397008] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar  5 19:06:58 mobile-3 kernel: [    0.397014] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Mar  5 19:06:58 mobile-3 kernel: [    0.397018] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Mar  5 19:06:58 mobile-3 kernel: [    0.400023] Switching to clocksource tsc
Mar  5 19:06:58 mobile-3 kernel: [    0.401694] AppArmor: AppArmor Filesystem Enabled
Mar  5 19:06:58 mobile-3 kernel: [    0.401704] pnp: PnP ACPI init
Mar  5 19:06:58 mobile-3 kernel: [    0.401713] ACPI: bus type pnp registered
Mar  5 19:06:58 mobile-3 kernel: [    0.416153] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Mar  5 19:06:58 mobile-3 kernel: [    0.416156] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Mar  5 19:06:58 mobile-3 kernel: [    0.416232] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Mar  5 19:06:58 mobile-3 kernel: [    0.416235] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Mar  5 19:06:58 mobile-3 kernel: [    0.416238] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Mar  5 19:06:58 mobile-3 kernel: [    0.433675] pnp: PnP ACPI: found 13 devices
Mar  5 19:06:58 mobile-3 kernel: [    0.433677] ACPI: ACPI bus type pnp unregistered
Mar  5 19:06:58 mobile-3 kernel: [    0.433691] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433693] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433701] system 00:06: ioport range 0xc80-0xcff could not be reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433706] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433712] system 00:0a: ioport range 0x900-0x97f has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433714] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433720] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433722] system 00:0b: ioport range 0x1080-0x10bf has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433724] system 00:0b: ioport range 0x10c0-0x10df has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433726] system 00:0b: ioport range 0x809-0x809 has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433731] system 00:0c: iomem range 0x0-0x9efff could not be reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433733] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433736] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433738] system 00:0c: iomem range 0xe0000-0xfffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433740] system 00:0c: iomem range 0x100000-0xdfe71fff could not be reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433742] system 00:0c: iomem range 0xdfe72000-0xdfefffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433744] system 00:0c: iomem range 0xdff00000-0xdfffffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433747] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433749] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433751] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433754] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433756] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433758] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433761] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433763] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433765] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433767] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.433769] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
Mar  5 19:06:58 mobile-3 kernel: [    0.438509] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar  5 19:06:58 mobile-3 kernel: [    0.438512] pci 0000:00:01.0:   IO window: 0xe000-0xefff
Mar  5 19:06:58 mobile-3 kernel: [    0.438515] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438518] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438523] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
Mar  5 19:06:58 mobile-3 kernel: [    0.438526] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
Mar  5 19:06:58 mobile-3 kernel: [    0.438532] pci 0000:00:1c.0:   MEM window: 0xf1f00000-0xf1ffffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438537] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0200000-0x000000f03fffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438545] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
Mar  5 19:06:58 mobile-3 kernel: [    0.438548] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
Mar  5 19:06:58 mobile-3 kernel: [    0.438554] pci 0000:00:1c.1:   MEM window: 0xf1e00000-0xf1efffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438559] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438566] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
Mar  5 19:06:58 mobile-3 kernel: [    0.438569] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
Mar  5 19:06:58 mobile-3 kernel: [    0.438575] pci 0000:00:1c.4:   MEM window: 0xf1c00000-0xf1dfffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438580] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438588] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Mar  5 19:06:58 mobile-3 kernel: [    0.438589] pci 0000:00:1e.0:   IO window: disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.438595] pci 0000:00:1e.0:   MEM window: 0xf1b00000-0xf1bfffff
Mar  5 19:06:58 mobile-3 kernel: [    0.438600] pci 0000:00:1e.0:   PREFETCH window: disabled
Mar  5 19:06:58 mobile-3 kernel: [    0.438615]   alloc irq_desc for 16 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.438617]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.438622] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.438626] pci 0000:00:01.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.438635] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.438640] pci 0000:00:1c.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.438649]   alloc irq_desc for 17 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.438651]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.438653] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 19:06:58 mobile-3 kernel: [    0.438658] pci 0000:00:1c.1: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.438668] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.438672] pci 0000:00:1c.4: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.438680] pci 0000:00:1e.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.438685] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438687] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438689] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438691] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438693] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438695] pci_bus 0000:09: resource 0 io:  [0xd000-0xdfff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438697] pci_bus 0000:09: resource 1 mem: [0xf1f00000-0xf1ffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438699] pci_bus 0000:09: resource 2 pref mem [0xf0200000-0xf03fffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438701] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438703] pci_bus 0000:0b: resource 1 mem: [0xf1e00000-0xf1efffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438705] pci_bus 0000:0b: resource 2 pref mem [0xf0400000-0xf05fffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438707] pci_bus 0000:0c: resource 0 io:  [0xc000-0xcfff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438709] pci_bus 0000:0c: resource 1 mem: [0xf1c00000-0xf1dfffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438711] pci_bus 0000:0c: resource 2 pref mem [0xf0000000-0xf01fffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438713] pci_bus 0000:03: resource 1 mem: [0xf1b00000-0xf1bfffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438715] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438717] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Mar  5 19:06:58 mobile-3 kernel: [    0.438751] NET: Registered protocol family 2
Mar  5 19:06:58 mobile-3 kernel: [    0.438902] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.440150] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.444676] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.445283] TCP: Hash tables configured (established 524288 bind 65536)
Mar  5 19:06:58 mobile-3 kernel: [    0.445286] TCP reno registered
Mar  5 19:06:58 mobile-3 kernel: [    0.445408] NET: Registered protocol family 1
Mar  5 19:06:58 mobile-3 kernel: [    0.445600] pci 0000:01:00.0: Boot video device
Mar  5 19:06:58 mobile-3 kernel: [    0.445651] Simple Boot Flag at 0x79 set to 0x1
Mar  5 19:06:58 mobile-3 kernel: [    0.445815] Scanning for low memory corruption every 60 seconds
Mar  5 19:06:58 mobile-3 kernel: [    0.445973] audit: initializing netlink socket (disabled)
Mar  5 19:06:58 mobile-3 kernel: [    0.445983] type=2000 audit(1330974402.439:1): initialized
Mar  5 19:06:58 mobile-3 kernel: [    0.454157] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar  5 19:06:58 mobile-3 kernel: [    0.455308] VFS: Disk quotas dquot_6.5.2
Mar  5 19:06:58 mobile-3 kernel: [    0.455354] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar  5 19:06:58 mobile-3 kernel: [    0.455853] fuse init (API version 7.13)
Mar  5 19:06:58 mobile-3 kernel: [    0.455919] msgmni has been set to 7905
Mar  5 19:06:58 mobile-3 kernel: [    0.456106] alg: No test for stdrng (krng)
Mar  5 19:06:58 mobile-3 kernel: [    0.456148] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Mar  5 19:06:58 mobile-3 kernel: [    0.456150] io scheduler noop registered
Mar  5 19:06:58 mobile-3 kernel: [    0.456152] io scheduler anticipatory registered
Mar  5 19:06:58 mobile-3 kernel: [    0.456154] io scheduler deadline registered
Mar  5 19:06:58 mobile-3 kernel: [    0.456209] io scheduler cfq registered (default)
Mar  5 19:06:58 mobile-3 kernel: [    0.456338]   alloc irq_desc for 24 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456339]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456348] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.456353] pcieport 0000:00:01.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.456470]   alloc irq_desc for 25 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456471]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456479] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.456490] pcieport 0000:00:1c.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.456638]   alloc irq_desc for 26 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456640]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456648] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.456658] pcieport 0000:00:1c.1: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.456801]   alloc irq_desc for 27 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456802]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.456810] pcieport 0000:00:1c.4: irq 27 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.456821] pcieport 0000:00:1c.4: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.456916] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  5 19:06:58 mobile-3 kernel: [    0.457014] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar  5 19:06:58 mobile-3 kernel: [    0.457142] ACPI: AC Adapter [AC] (on-line)
Mar  5 19:06:58 mobile-3 kernel: [    0.457207] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Mar  5 19:06:58 mobile-3 kernel: [    0.605650] ACPI: Lid Switch [LID]
Mar  5 19:06:58 mobile-3 kernel: [    0.605687] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Mar  5 19:06:58 mobile-3 kernel: [    0.605693] ACPI: Power Button [PBTN]
Mar  5 19:06:58 mobile-3 kernel: [    0.605728] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Mar  5 19:06:58 mobile-3 kernel: [    0.605730] ACPI: Sleep Button [SBTN]
Mar  5 19:06:58 mobile-3 kernel: [    0.606281] ACPI: SSDT 00000000dfe72cb4 002C8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.606667] ACPI: SSDT 00000000dfe7264a 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.607079] Monitor-Mwait will be used to enter C-1 state
Mar  5 19:06:58 mobile-3 kernel: [    0.620096] Monitor-Mwait will be used to enter C-2 state
Mar  5 19:06:58 mobile-3 kernel: [    0.620122] Monitor-Mwait will be used to enter C-3 state
Mar  5 19:06:58 mobile-3 kernel: [    0.620127] Marking TSC unstable due to TSC halts in idle
Mar  5 19:06:58 mobile-3 kernel: [    0.620179] processor LNXCPU:00: registered as cooling_device0
Mar  5 19:06:58 mobile-3 kernel: [    0.620491] ACPI: SSDT 00000000dfe72f7c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.620718] ACPI: SSDT 00000000dfe72c2f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Mar  5 19:06:58 mobile-3 kernel: [    0.621049] processor LNXCPU:01: registered as cooling_device1
Mar  5 19:06:58 mobile-3 kernel: [    0.623045] thermal LNXTHERM:01: registered as thermal_zone0
Mar  5 19:06:58 mobile-3 kernel: [    0.623052] ACPI: Thermal Zone [THM] (59 C)
Mar  5 19:06:58 mobile-3 kernel: [    0.624216] Linux agpgart interface v0.103
Mar  5 19:06:58 mobile-3 kernel: [    0.624245] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar  5 19:06:58 mobile-3 kernel: [    0.625311] brd: module loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.625706] loop: module loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.625767] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Mar  5 19:06:58 mobile-3 kernel: [    0.625848] ata_piix 0000:00:1f.1: version 2.13
Mar  5 19:06:58 mobile-3 kernel: [    0.625860] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.625898] ata_piix 0000:00:1f.1: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.625973] scsi0 : ata_piix
Mar  5 19:06:58 mobile-3 kernel: [    0.626028] scsi1 : ata_piix
Mar  5 19:06:58 mobile-3 kernel: [    0.626503] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Mar  5 19:06:58 mobile-3 kernel: [    0.626505] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Mar  5 19:06:58 mobile-3 kernel: [    0.626761] Fixed MDIO Bus: probed
Mar  5 19:06:58 mobile-3 kernel: [    0.626789] PPP generic driver version 2.4.2
Mar  5 19:06:58 mobile-3 kernel: [    0.626814] tun: Universal TUN/TAP device driver, 1.6
Mar  5 19:06:58 mobile-3 kernel: [    0.626816] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar  5 19:06:58 mobile-3 kernel: [    0.626882] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar  5 19:06:58 mobile-3 kernel: [    0.626899]   alloc irq_desc for 22 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.626901]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.626906] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Mar  5 19:06:58 mobile-3 kernel: [    0.626918] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.626921] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.626951] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Mar  5 19:06:58 mobile-3 kernel: [    0.626988] ehci_hcd 0000:00:1a.7: debug port 1
Mar  5 19:06:58 mobile-3 kernel: [    0.630890] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Mar  5 19:06:58 mobile-3 kernel: [    0.630923] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
Mar  5 19:06:58 mobile-3 kernel: [    0.635264] ata2: port disabled. ignoring.
Mar  5 19:06:58 mobile-3 kernel: [    0.635411] Switching to clocksource hpet
Mar  5 19:06:58 mobile-3 kernel: [    0.652752] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Mar  5 19:06:58 mobile-3 kernel: [    0.652962] usb usb1: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.652988] hub 1-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.652995] hub 1-0:1.0: 4 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.653184]   alloc irq_desc for 20 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.653186]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.653190] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 19:06:58 mobile-3 kernel: [    0.653203] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.653206] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.653232] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Mar  5 19:06:58 mobile-3 kernel: [    0.653271] ehci_hcd 0000:00:1d.7: debug port 1
Mar  5 19:06:58 mobile-3 kernel: [    0.655555] ACPI: Battery Slot [BAT0] (battery present)
Mar  5 19:06:58 mobile-3 kernel: [    0.657279] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Mar  5 19:06:58 mobile-3 kernel: [    0.657291] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
Mar  5 19:06:58 mobile-3 kernel: [    0.670620] Freeing initrd memory: 8172k freed
Mar  5 19:06:58 mobile-3 kernel: [    0.680412] ata1.00: ATAPI: Optiarc DVD+/-RW AD-7640A, JD06, max UDMA/33
Mar  5 19:06:58 mobile-3 kernel: [    0.682535] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Mar  5 19:06:58 mobile-3 kernel: [    0.682695] usb usb2: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.682725] hub 2-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.682738] hub 2-0:1.0: 6 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.682805] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar  5 19:06:58 mobile-3 kernel: [    0.682822] uhci_hcd: USB Universal Host Controller Interface driver
Mar  5 19:06:58 mobile-3 kernel: [    0.682871] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 19:06:58 mobile-3 kernel: [    0.682882] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.682885] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.682922] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Mar  5 19:06:58 mobile-3 kernel: [    0.682956] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
Mar  5 19:06:58 mobile-3 kernel: [    0.683033] usb usb3: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.683063] hub 3-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.683070] hub 3-0:1.0: 2 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.683110]   alloc irq_desc for 21 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.683112]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.683119] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar  5 19:06:58 mobile-3 kernel: [    0.683125] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.683128] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.683154] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Mar  5 19:06:58 mobile-3 kernel: [    0.683192] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
Mar  5 19:06:58 mobile-3 kernel: [    0.683278] usb usb4: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.683301] hub 4-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.683307] hub 4-0:1.0: 2 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.683348] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 19:06:58 mobile-3 kernel: [    0.683354] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.683357] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.683385] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Mar  5 19:06:58 mobile-3 kernel: [    0.683411] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
Mar  5 19:06:58 mobile-3 kernel: [    0.683486] usb usb5: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.683505] hub 5-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.683511] hub 5-0:1.0: 2 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.683552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar  5 19:06:58 mobile-3 kernel: [    0.683558] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.683561] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.683585] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Mar  5 19:06:58 mobile-3 kernel: [    0.683612] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
Mar  5 19:06:58 mobile-3 kernel: [    0.683688] usb usb6: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.683709] hub 6-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.683714] hub 6-0:1.0: 2 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.683759] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Mar  5 19:06:58 mobile-3 kernel: [    0.683765] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.683768] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  5 19:06:58 mobile-3 kernel: [    0.683793] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Mar  5 19:06:58 mobile-3 kernel: [    0.683821] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
Mar  5 19:06:58 mobile-3 kernel: [    0.683898] usb usb7: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    0.683916] hub 7-0:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    0.683922] hub 7-0:1.0: 2 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    0.684005] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar  5 19:06:58 mobile-3 kernel: [    0.697382] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  5 19:06:58 mobile-3 kernel: [    0.697388] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar  5 19:06:58 mobile-3 kernel: [    0.697468] mice: PS/2 mouse device common for all mice
Mar  5 19:06:58 mobile-3 kernel: [    0.697577] rtc_cmos 00:04: RTC can wake from S4
Mar  5 19:06:58 mobile-3 kernel: [    0.697626] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Mar  5 19:06:58 mobile-3 kernel: [    0.697657] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1039) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 kernel: [    0.697756] device-mapper: uevent: version 1.0.3
Mar  5 19:06:58 mobile-3 kernel: [    0.697861] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Mar  5 19:06:58 mobile-3 kernel: [    0.697921] device-mapper: multipath: version 1.1.0 loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.697924] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar  5 19:06:58 mobile-3 kernel: [    0.698111] cpuidle: using governor ladder
Mar  5 19:06:58 mobile-3 kernel: [    0.698687] cpuidle: using governor menu
Mar  5 19:06:58 mobile-3 kernel: [    0.698977] TCP cubic registered
Mar  5 19:06:58 mobile-3 kernel: [    0.699103] NET: Registered protocol family 10
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1047) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1053) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Successfully dropped root privileges.
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: avahi-daemon 0.6.25 starting up.
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1057) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  starting...
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Successfully called chroot().
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1064) terminated with status 127
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  Trying to start the modem-manager...
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Successfully dropped remaining capabilities.
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: init!
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:09:00.0/net/eth0, iface: eth0)
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/net/eth1, iface: eth1)
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar  5 19:06:58 mobile-3 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: No service file found in /etc/avahi/services.
Mar  5 19:06:58 mobile-3 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar  5 19:06:58 mobile-3 kernel: [    0.699699] NET: Registered protocol family 17
Mar  5 19:06:58 mobile-3 kernel: [    0.700816] PM: Resume from disk failed.
Mar  5 19:06:58 mobile-3 kernel: [    0.700828] registered taskstats version 1
Mar  5 19:06:58 mobile-3 kernel: [    0.701416]   Magic number: 4:436:141
Mar  5 19:06:58 mobile-3 kernel: [    0.701433] block ram6: hash matches
Mar  5 19:06:58 mobile-3 kernel: [    0.701476] acpi device:12: hash matches
Mar  5 19:06:58 mobile-3 kernel: [    0.701543] rtc_cmos 00:04: setting system clock to 2012-03-05 19:06:43 UTC (1330974403)
Mar  5 19:06:58 mobile-3 kernel: [    0.701546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar  5 19:06:58 mobile-3 kernel: [    0.701547] EDD information not available.
Mar  5 19:06:58 mobile-3 kernel: [    0.720393] ata1.00: configured for UDMA/33
Mar  5 19:06:58 mobile-3 kernel: [    0.723296] scsi 0:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640A JD06 PQ: 0 ANSI: 5
Mar  5 19:06:58 mobile-3 kernel: [    0.725073] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Mar  5 19:06:58 mobile-3 kernel: [    0.729805] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
Mar  5 19:06:58 mobile-3 kernel: [    0.729810] Uniform CD-ROM driver Revision: 3.20
Mar  5 19:06:58 mobile-3 kernel: [    0.729957] sr 0:0:0:0: Attached scsi CD-ROM sr0
Mar  5 19:06:58 mobile-3 kernel: [    0.729993] sr 0:0:0:0: Attached scsi generic sg0 type 5
Mar  5 19:06:58 mobile-3 kernel: [    0.730077] Freeing unused kernel memory: 884k freed
Mar  5 19:06:58 mobile-3 kernel: [    0.730517] Write protecting the kernel read-only data: 7716k
Mar  5 19:06:58 mobile-3 kernel: [    0.742606] udev: starting version 151
Mar  5 19:06:58 mobile-3 kernel: [    0.813568] ahci 0000:00:1f.2: version 3.0
Mar  5 19:06:58 mobile-3 kernel: [    0.813588] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 19:06:58 mobile-3 kernel: [    0.813642]   alloc irq_desc for 28 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.813643]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.813655] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.813724] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
Mar  5 19:06:58 mobile-3 kernel: [    0.813727] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
Mar  5 19:06:58 mobile-3 kernel: [    0.813733] ahci 0000:00:1f.2: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.815962] sky2 driver version 1.25
Mar  5 19:06:58 mobile-3 kernel: [    0.815991] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.816003] sky2 0000:09:00.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [    0.816033] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
Mar  5 19:06:58 mobile-3 kernel: [    0.816138]   alloc irq_desc for 29 on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.816139]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [    0.816154] sky2 0000:09:00.0: irq 29 for MSI/MSI-X
Mar  5 19:06:58 mobile-3 kernel: [    0.816656] sky2 eth0: addr 00:21:9b:e7:68:9e
Mar  5 19:06:58 mobile-3 kernel: [    0.842370] scsi2 : ahci
Mar  5 19:06:58 mobile-3 kernel: [    0.846968] scsi3 : ahci
Mar  5 19:06:58 mobile-3 kernel: [    0.847063] scsi4 : ahci
Mar  5 19:06:58 mobile-3 kernel: [    0.847269] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 28
Mar  5 19:06:58 mobile-3 kernel: [    0.847271] ata4: DUMMY
Mar  5 19:06:58 mobile-3 kernel: [    0.847274] ata5: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 28
Mar  5 19:06:58 mobile-3 kernel: [    0.847968] ohci1394 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 19:06:58 mobile-3 kernel: [    0.904689] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Mar  5 19:06:58 mobile-3 kernel: [    0.970079] usb 1-1: new high speed USB device using ehci_hcd and address 2
Mar  5 19:06:58 mobile-3 kernel: [    1.125256] usb 1-1: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Mar  5 19:06:58 mobile-3 kernel: [    1.190101] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  5 19:06:58 mobile-3 kernel: [    1.192592] ata5: SATA link down (SStatus 0 SControl 300)
Mar  5 19:06:58 mobile-3 kernel: [    1.265194] ata3.00: ATA-8: ST9250421ASG, DE13, max UDMA/133
Mar  5 19:06:58 mobile-3 kernel: [    1.265199] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
Mar  5 19:06:58 mobile-3 kernel: [    1.309432] ata3.00: configured for UDMA/133
Mar  5 19:06:58 mobile-3 kernel: [    1.320289] scsi 2:0:0:0: Direct-Access     ATA      ST9250421ASG     DE13 PQ: 0 ANSI: 5
Mar  5 19:06:58 mobile-3 kernel: [    1.320408] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Mar  5 19:06:58 mobile-3 kernel: [    1.320411] sd 2:0:0:0: Attached scsi generic sg1 type 0
Mar  5 19:06:58 mobile-3 kernel: [    1.320556] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 19:06:58 mobile-3 kernel: [    1.320559] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar  5 19:06:58 mobile-3 kernel: [    1.320631] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: (25663776) ... get_connections.
Mar  5 19:06:58 mobile-3 NetworkManager:    SCPlugin-Ifupdown: (25663776) ... get_connections (managed=false): return empty list.
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1090) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process ended, respawning
Mar  5 19:06:58 mobile-3 kernel: [    1.320924]  sda: sda1 sda2 sda3 sda4
Mar  5 19:06:58 mobile-3 kernel: [    1.360075] usb 2-1: new high speed USB device using ehci_hcd and address 2
Mar  5 19:06:58 mobile-3 kernel: [    1.361151] sd 2:0:0:0: [sda] Attached SCSI disk
Mar  5 19:06:58 mobile-3 kernel: [    1.514220] usb 2-1: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    1.514515] hub 2-1:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    1.514857] hub 2-1:1.0: 4 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    1.889228] EXT4-fs (sda1): mounted filesystem with ordered data mode
Mar  5 19:06:58 mobile-3 kernel: [    1.912548] usb 3-2: new full speed USB device using uhci_hcd and address 2
Mar  5 19:06:58 mobile-3 kernel: [    2.101156] usb 3-2: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    2.220458] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc000342c41e1]
Mar  5 19:06:58 mobile-3 kernel: [    2.382549] usb 7-2: new full speed USB device using uhci_hcd and address 2
Mar  5 19:06:58 mobile-3 kernel: [    2.561983] usb 7-2: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    2.563934] hub 7-2:1.0: USB hub found
Mar  5 19:06:58 mobile-3 kernel: [    2.565895] hub 7-2:1.0: 3 ports detected
Mar  5 19:06:58 mobile-3 kernel: [    2.652896] usb 2-1.1: new low speed USB device using ehci_hcd and address 4
Mar  5 19:06:58 mobile-3 kernel: [    2.766968] usb 2-1.1: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    2.840641] usb 2-1.2: new high speed USB device using ehci_hcd and address 5
Mar  5 19:06:58 mobile-3 kernel: [    2.953613] usb 2-1.2: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    3.043900] usb 7-2.1: new full speed USB device using uhci_hcd and address 3
Mar  5 19:06:58 mobile-3 kernel: [    3.177033] usb 7-2.1: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    3.263884] usb 7-2.2: new full speed USB device using uhci_hcd and address 4
Mar  5 19:06:58 mobile-3 kernel: [    3.398025] usb 7-2.2: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [    3.481868] usb 7-2.3: new full speed USB device using uhci_hcd and address 5
Mar  5 19:06:58 mobile-3 kernel: [    3.617954] usb 7-2.3: configuration #1 chosen from 1 choice
Mar  5 19:06:58 mobile-3 kernel: [   13.463553] udev: starting version 151
Mar  5 19:06:58 mobile-3 kernel: [   13.634176] Adding 4931944k swap on /dev/sda4.  Priority:-1 extents:1 across:4931944k 
Mar  5 19:06:58 mobile-3 kernel: [   13.677524] type=1505 audit(1330996016.470:2):  operation="profile_load" pid=606 name="/sbin/dhclient3"
Mar  5 19:06:58 mobile-3 kernel: [   13.678088] type=1505 audit(1330996016.470:3):  operation="profile_load" pid=606 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar  5 19:06:58 mobile-3 kernel: [   13.678398] type=1505 audit(1330996016.470:4):  operation="profile_load" pid=606 name="/usr/lib/connman/scripts/dhclient-script"
Mar  5 19:06:58 mobile-3 kernel: [   13.679553] type=1505 audit(1330996016.470:5):  operation="profile_replace" pid=618 name="/sbin/dhclient3"
Mar  5 19:06:58 mobile-3 kernel: [   13.680122] type=1505 audit(1330996016.470:6):  operation="profile_replace" pid=618 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar  5 19:06:58 mobile-3 kernel: [   13.680434] type=1505 audit(1330996016.470:7):  operation="profile_replace" pid=618 name="/usr/lib/connman/scripts/dhclient-script"
Mar  5 19:06:58 mobile-3 kernel: [   13.705240] lp: driver loaded but no devices found
Mar  5 19:06:58 mobile-3 kernel: [   13.796610] lib80211: common routines for IEEE802.11 drivers
Mar  5 19:06:58 mobile-3 kernel: [   13.796613] lib80211_crypt: registered algorithm 'NULL'
Mar  5 19:06:58 mobile-3 kernel: [   13.810036] vga16fb: initializing
Mar  5 19:06:58 mobile-3 kernel: [   13.810040] vga16fb: mapped to 0xffff8800000a0000
Mar  5 19:06:58 mobile-3 kernel: [   13.810166] fb0: VGA16 VGA frame buffer device
Mar  5 19:06:58 mobile-3 kernel: [   13.855630] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Mar  5 19:06:58 mobile-3 kernel: [   13.950203] wl: module license 'MIXED/Proprietary' taints kernel.
Mar  5 19:06:58 mobile-3 kernel: [   13.950207] Disabling lock debugging due to kernel taint
Mar  5 19:06:58 mobile-3 kernel: [   13.953525] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar  5 19:06:58 mobile-3 kernel: [   13.953537] wl 0000:0b:00.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [   13.970085] Bluetooth: Core ver 2.15
Mar  5 19:06:58 mobile-3 kernel: [   13.970127] NET: Registered protocol family 31
Mar  5 19:06:58 mobile-3 kernel: [   13.970128] Bluetooth: HCI device and connection manager initialized
Mar  5 19:06:58 mobile-3 kernel: [   13.970130] Bluetooth: HCI socket layer initialized
Mar  5 19:06:58 mobile-3 kernel: [   13.974617] usbcore: registered new interface driver hiddev
Mar  5 19:06:58 mobile-3 kernel: [   13.977748] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input5
Mar  5 19:06:58 mobile-3 kernel: [   13.990235] generic-usb 0003:046D:C03D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-1.1/input0
Mar  5 19:06:58 mobile-3 kernel: [   13.994089] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input6
Mar  5 19:06:58 mobile-3 kernel: [   13.994148] generic-usb 0003:0A5C:4502.0002: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0
Mar  5 19:06:58 mobile-3 kernel: [   13.998157] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input7
Mar  5 19:06:58 mobile-3 kernel: [   13.998227] generic-usb 0003:0A5C:4503.0003: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
Mar  5 19:06:58 mobile-3 kernel: [   13.998244] usbcore: registered new interface driver usbhid
Mar  5 19:06:58 mobile-3 kernel: [   13.998246] usbhid: v2.6:USB HID core driver
Mar  5 19:06:58 mobile-3 kernel: [   14.010241] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar  5 19:06:58 mobile-3 kernel: [   14.010337] usbcore: registered new interface driver btusb
Mar  5 19:06:58 mobile-3 kernel: [   14.026839] sdhci: Secure Digital Host Controller Interface driver
Mar  5 19:06:58 mobile-3 kernel: [   14.026842] sdhci: Copyright(c) Pierre Ossman
Mar  5 19:06:58 mobile-3 kernel: [   14.032075] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
Mar  5 19:06:58 mobile-3 kernel: [   14.032096]   alloc irq_desc for 18 on node -1
Mar  5 19:06:58 mobile-3 kernel: [   14.032097]   alloc kstat_irqs on node -1
Mar  5 19:06:58 mobile-3 kernel: [   14.032103] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Mar  5 19:06:58 mobile-3 kernel: [   14.034334] Registered led device: mmc0::
Mar  5 19:06:58 mobile-3 kernel: [   14.035418] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
Mar  5 19:06:58 mobile-3 kernel: [   14.053021] Linux video capture interface: v2.00
Mar  5 19:06:58 mobile-3 kernel: [   14.057015] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
Mar  5 19:06:58 mobile-3 kernel: [   14.057382] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Mar  5 19:06:58 mobile-3 kernel: [   14.058034] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input8
Mar  5 19:06:58 mobile-3 kernel: [   14.058092] usbcore: registered new interface driver uvcvideo
Mar  5 19:06:58 mobile-3 kernel: [   14.058119] USB Video Class driver (v0.1.0)
Mar  5 19:06:58 mobile-3 kernel: [   14.151689] input: Dell WMI hotkeys as /devices/virtual/input/input9
Mar  5 19:06:58 mobile-3 kernel: [   14.173069] lib80211_crypt: registered algorithm 'TKIP'
Mar  5 19:06:58 mobile-3 kernel: [   14.173529] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
Mar  5 19:06:58 mobile-3 kernel: [   14.222048] acpi device:30: registered as cooling_device2
Mar  5 19:06:58 mobile-3 kernel: [   14.223102] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2d/LNXVIDEO:00/input/input10
Mar  5 19:06:58 mobile-3 kernel: [   14.223181] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Mar  5 19:06:58 mobile-3 kernel: [   14.270450] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
Mar  5 19:06:58 mobile-3 kernel: [   14.295956] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
Mar  5 19:06:58 mobile-3 kernel: [   14.391913] Console: switching to colour frame buffer device 80x30
Mar  5 19:06:58 mobile-3 kernel: [   15.090605] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Mar  5 19:06:58 mobile-3 kernel: [   15.090643] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar  5 19:06:58 mobile-3 kernel: [   15.247527] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
Mar  5 19:06:58 mobile-3 kernel: [   15.548003] type=1505 audit(1330996018.340:8):  operation="profile_load" pid=1079 name="/usr/share/gdm/guest-session/Xsession"
Mar  5 19:06:58 mobile-3 kernel: [   15.548184] type=1505 audit(1330996018.340:9):  operation="profile_replace" pid=1080 name="/sbin/dhclient3"
Mar  5 19:06:58 mobile-3 kernel: [   15.548760] type=1505 audit(1330996018.340:10):  operation="profile_replace" pid=1080 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar  5 19:06:58 mobile-3 kernel: [   15.549075] type=1505 audit(1330996018.340:11):  operation="profile_replace" pid=1080 name="/usr/lib/connman/scripts/dhclient-script"
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Network interface enumeration completed.
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Registering HINFO record with values 'X86_64'/'LINUX'.
Mar  5 19:06:58 mobile-3 avahi-daemon[1056]: Server startup complete. Host name is mobile-3.local. Local service cookie is 2337218944.
Mar  5 19:06:58 mobile-3 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): carrier is OFF
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): now managed
Mar  5 19:06:58 mobile-3 kernel: [   15.590423] sky2 eth0: enabling interface
Mar  5 19:06:58 mobile-3 kernel: [   15.590822] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  5 19:06:58 mobile-3 kernel: [   15.750110] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar  5 19:06:58 mobile-3 kernel: [   15.750183] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Mar  5 19:06:58 mobile-3 kernel: [   15.750232] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): bringing up device.
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): preparing device.
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): now managed
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): bringing up device.
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Generic
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Ericsson MBM
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Gobi
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin AnyData
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Novatel
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Option High-Speed
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Sierra
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Huawei
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Nokia
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin ZTE
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Longcheer
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin MotoC
Mar  5 19:06:58 mobile-3 modem-manager: Loaded plugin Option
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): preparing device.
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Mar  5 19:06:58 mobile-3 NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Mar  5 19:06:58 mobile-3 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  modem-manager is now available
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  Trying to start the supplicant...
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Mar  5 19:06:58 mobile-3 NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Mar  5 19:06:58 mobile-3 init: mythtv-backend main process (1093) terminated with status 127
Mar  5 19:06:58 mobile-3 init: mythtv-backend respawning too fast, stopped
Mar  5 19:06:58 mobile-3 init: apport pre-start process (1129) terminated with status 1
Mar  5 19:06:58 mobile-3 cron[1136]: (CRON) INFO (pidfile fd = 3)
Mar  5 19:06:58 mobile-3 acpid: starting up with proc fs
Mar  5 19:06:58 mobile-3 acpid: 36 rules loaded
Mar  5 19:06:58 mobile-3 anacron[1178]: Anacron 2.3 started on 2012-03-05
Mar  5 19:06:58 mobile-3 acpid: waiting for events: event logging is off
Mar  5 19:06:58 mobile-3 init: apport post-stop process (1174) terminated with status 1
Mar  5 19:06:58 mobile-3 cron[1186]: (CRON) STARTUP (fork ok)
Mar  5 19:06:58 mobile-3 cron[1186]: (CRON) INFO (Running @reboot jobs)
Mar  5 19:06:58 mobile-3 gdm-binary[1189]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:58 mobile-3 anacron[1178]: Normal exit (0 jobs run)
Mar  5 19:06:58 mobile-3 gdm-binary[1189]: WARNING: Unable to find users: no seat-id found
Mar  5 19:06:58 mobile-3 gdm-simple-slave[1268]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:58 mobile-3 acpid: client connected from 1313[0:0]
Mar  5 19:06:58 mobile-3 acpid: 1 client rule loaded
Mar  5 19:06:59 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.601059 seconds
Mar  5 19:06:59 mobile-3 gdm-simple-slave[1333]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:59 mobile-3 acpid: client 1313[0:0] has disconnected
Mar  5 19:06:59 mobile-3 acpid: client connected from 1335[0:0]
Mar  5 19:06:59 mobile-3 acpid: 1 client rule loaded
Mar  5 19:06:59 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.350029 seconds
Mar  5 19:06:59 mobile-3 gdm-simple-slave[1351]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:59 mobile-3 acpid: client 1335[0:0] has disconnected
Mar  5 19:06:59 mobile-3 acpid: client connected from 1353[0:0]
Mar  5 19:06:59 mobile-3 acpid: 1 client rule loaded
Mar  5 19:06:59 mobile-3 kernel: [   16.932317] vboxdrv: Found 2 processor cores.
Mar  5 19:06:59 mobile-3 kernel: [   16.932969] VBoxDrv: dbg - g_abExecMemory=ffffffffa04183a0
Mar  5 19:06:59 mobile-3 kernel: [   16.932985] vboxdrv: fAsync=0 offMin=0x1db offMax=0x9d0
Mar  5 19:06:59 mobile-3 kernel: [   16.933038] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Mar  5 19:06:59 mobile-3 kernel: [   16.933040] vboxdrv: Successfully loaded version 4.1.8 (interface 0x00190000).
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1374]: Upgrading MySQL tables if necessary.
Mar  5 19:06:59 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.160594 seconds
Mar  5 19:06:59 mobile-3 gdm-simple-slave[1381]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1377]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1377]: Looking for 'mysql' as: /usr/bin/mysql
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1377]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1377]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1387]: Checking for insecure root accounts.
Mar  5 19:06:59 mobile-3 /etc/mysql/debian-start[1393]: Triggering myisam-recover for all MyISAM tables
Mar  5 19:06:59 mobile-3 avahi-daemon[1056]: Registering new address record for fe80::223:4dff:fe20:1da3 on eth1.*.
Mar  5 19:06:59 mobile-3 acpid: client 1353[0:0] has disconnected
Mar  5 19:06:59 mobile-3 acpid: client connected from 1391[0:0]
Mar  5 19:06:59 mobile-3 acpid: 1 client rule loaded
Mar  5 19:06:59 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.122327 seconds
Mar  5 19:06:59 mobile-3 gdm-simple-slave[1400]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:06:59 mobile-3 acpid: client 1391[0:0] has disconnected
Mar  5 19:06:59 mobile-3 acpid: client connected from 1402[0:0]
Mar  5 19:06:59 mobile-3 acpid: 1 client rule loaded
Mar  5 19:07:00 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.124316 seconds
Mar  5 19:07:00 mobile-3 gdm-simple-slave[1413]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  5 19:07:00 mobile-3 acpid: client 1402[0:0] has disconnected
Mar  5 19:07:00 mobile-3 acpid: client connected from 1416[0:0]
Mar  5 19:07:00 mobile-3 acpid: 1 client rule loaded
Mar  5 19:07:00 mobile-3 kernel: [   17.314105] vboxpci: IOMMU not found (not compiled)
Mar  5 19:07:00 mobile-3 gdm-binary[1189]: WARNING: GdmDisplay: display lasted 0.121390 seconds
Mar  5 19:07:00 mobile-3 gdm-binary[1189]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Mar  5 19:07:00 mobile-3 bluetoothd[1434]: Bluetooth daemon 4.60
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Starting SDP server
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Starting experimental netlink support
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Failed to find Bluetooth netlink family
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Failed to init netlink plugin
Mar  5 19:07:00 mobile-3 kernel: [   17.389688] Bluetooth: L2CAP ver 2.14
Mar  5 19:07:00 mobile-3 kernel: [   17.389691] Bluetooth: L2CAP socket layer initialized
Mar  5 19:07:00 mobile-3 kernel: [   17.441204] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 19:07:00 mobile-3 kernel: [   17.441206] Bluetooth: BNEP filters: protocol multicast
Mar  5 19:07:00 mobile-3 kernel: [   17.449780] ppdev: user-space parallel port driver
Mar  5 19:07:00 mobile-3 init: gdm main process (1189) terminated with status 1
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: bridge pan0 created
Mar  5 19:07:00 mobile-3 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Mar  5 19:07:00 mobile-3 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
Mar  5 19:07:00 mobile-3 NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
Mar  5 19:07:00 mobile-3 kernel: [   17.634121] Bridge firewalling registered
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: HCI dev 0 registered
Mar  5 19:07:00 mobile-3 kernel: [   17.661134] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 19:07:00 mobile-3 kernel: [   17.661136] Bluetooth: SCO socket layer initialized
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: HCI dev 0 up
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Starting security manager 0
Mar  5 19:07:00 mobile-3 anacron[1600]: Anacron 2.3 started on 2012-03-05
Mar  5 19:07:00 mobile-3 anacron[1600]: Normal exit (0 jobs run)
Mar  5 19:07:00 mobile-3 acpid: client 1416[0:0] has disconnected
Mar  5 19:07:00 mobile-3 acpid: client connected from 1606[0:0]
Mar  5 19:07:00 mobile-3 acpid: 1 client rule loaded
Mar  5 19:07:00 mobile-3 bluetoothd[1437]: Adapter /org/bluez/1434/hci0 has been enabled
Mar  5 19:07:00 mobile-3 kernel: [   17.785933] Bluetooth: RFCOMM TTY layer initialized
Mar  5 19:07:00 mobile-3 kernel: [   17.785938] Bluetooth: RFCOMM socket layer initialized
Mar  5 19:07:00 mobile-3 kernel: [   17.785940] Bluetooth: RFCOMM ver 1.11
Mar  5 19:07:00 mobile-3 init: plymouth-stop pre-start process (1661) terminated with status 1
Mar  5 19:07:03 mobile-3 wpa_supplicant[1147]: WPS-AP-AVAILABLE 
Mar  5 19:07:08 mobile-3 kernel: [   26.031713] eth1: no IPv6 routers present
Mar  5 19:07:24 mobile-3 wpa_supplicant[1147]: WPS-AP-AVAILABLE 
Mar  5 19:07:33 mobile-3 kernel: [   50.301479] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input17
Mar  5 19:07:45 mobile-3 kernel: [   63.132054] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input18
Mar  5 19:07:54 mobile-3 wpa_supplicant[1147]: WPS-AP-AVAILABLE 
Mar  5 19:08:12 mobile-3 kernel: [   89.462880] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input19
Mar  5 19:08:24 mobile-3 kernel: [  101.541041] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input20
Mar  5 19:08:33 mobile-3 init: tty2 main process ended, respawning
Mar  5 19:08:34 mobile-3 wpa_supplicant[1147]: WPS-AP-AVAILABLE 
Mar  5 19:08:46 mobile-3 kernel: Kernel logging (proc) stopped.
Mar  5 19:09:20 mobile-3 kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

I look over the logs and on the auth.log it shows when the update completed. I couldn't find any helpful info on the syslog, but I'm not an expert. 
Thanks

---

### Post by matt_symes on 2012-03-09
Hi

A "PAM pam_parse: expecting return value;" error seems to be the cause of the issue.

It's not an error i have ever seen but it gives a starting point for debugging and others may have come across it.

Let's have a look at these files.

```
cat /etc/pam.d/gdm
```

```
cat /etc/pam.d/gdm-autologin
```

Can you also post the output of this command.

```
grep -i "sucess=2 default=ignore" /etc/pam.d/*
```

Kind regards

---

### Post by kikotiger on 2012-03-09
Here is the output for gdm:
```

root@mobile-3:~# cat /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

This is for gdm-autologin:
```

root@mobile-3:~# cat /etc/pam.d/gdm-autologin
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
@include common-password

```

And this is for last command:
```

root@mobile-3:~# grep -i "sucess=2 default=ignore" /etc/pam.d/*
/etc/pam.d/common-auth:auth	[sucess=2 default=ignore] pam_thinkfinger.so

```

I also included the common-auth file:
```

root@mobile-3:~# cat /etc/pam.d/common-auth
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[sucess=2 default=ignore] pam_thinkfinger.so 
auth	[success=1 default=ignore]	pam_unix.so nullok_secure try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```
Thanks for taking the time helping me out solve this problem.

---

### Post by kikotiger on 2012-03-09
I do have a finger-print scanner, but neither using it nor entering the password works. I installed thinkfinger a while back and I have updated the kernel at least twice, so I don't think it might be that. But let me know if you have any ideas or suggestions.

---

### Post by matt_symes on 2012-03-09
Hi

> **kikotiger said:**
> I do have a finger-print scanner, but neither using it nor entering the password works. I installed thinkfinger a while back and I have updated the kernel at least twice, so I don't think it might be that. But let me know if you have any ideas or suggestions.

Interesting. A finger print scanner.

Here is my common-auth file. It's for 12.04 Precise install.

```
matthew@matthew-Aspire-7540:/etc/pam.d$ less /etc/pam.d/common-auth
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_cap.so 
# end of pam-auth-update config
matthew@matthew-Aspire-7540:/etc/pam.d$ 
```

Almost excatly the same apart from that pam_thinkfinger.so and pam_cap.so. I'm not saying use mine however see if you can get one for you Ubuntu version.

You could even try commenting out the pam_thinkfinger.so line and seeing if that helps.

Kind regards

---

### Post by kikotiger on 2012-03-09
Turns out it was that line that was preventing me from logging in, I commented it out and I was able to log in again. I did have to disable automatic login and set up a new password as I could not do any administrative actions.
Thanks a lot Matt, you saved me from reinstalling and loosing all my configurations. :)

---

