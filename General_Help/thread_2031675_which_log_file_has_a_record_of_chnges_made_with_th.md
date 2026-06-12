---
title: "which log file has a record of chnges made with the admin password?"
date: 2012-07-22
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-07-22
Hi All,

Last evening I had to give my daughter the administrative password over the phone so she could connect to a wireless access point in her area.

I want to make sure she didn't make other changes, she's just old enough to realize there might be ways to circumvent our parental responsibility that we use to keep her safe.

I expected to find the log for such activity on the subdoers file, but it doesn't contain any record(s) of past administrative changes.

Which file has a list of all changes made using the sudo command??

TY/

Art

---

### Post by Doug S on 2012-07-22
You might find what you are looking for in /var/log/auth.log
By default the file rotates on Sunday morning (at least mine do), so you might also need to look at /var/log/auth.log.1

---

### Post by goodbye-windows(tm) on 2012-07-22
Hi Doug,

Found the log with no difficulty. TY.

Here's the portion of the log that deals with the time period she had access to the computer with my password. Note that I am adminhannah. So, it looks like she logged into my account instead of making the changed from her account. Her account is 'hannah'.

> Jul 22 18:34:37 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm-autologin:account): could not identify user (from getpwnam(grammy))

Jul 22 18:34:37 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)

Jul 22 18:34:37 hannahadmin-Inspiron-N5110 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0

Jul 22 18:34:39 hannahadmin-Inspiron-N5110 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hannah"

Jul 22 18:34:39 hannahadmin-Inspiron-N5110 dbus[939]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.24" (uid=104 pid=1428 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1269 comm="/usr/sbin/console-kit-daemon --no-daemon ")

Jul 22 18:34:48 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm:auth): conversation failed

Jul 22 18:34:48 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm:auth): auth could not identify password for [hannah]

Jul 22 18:34:48 hannahadmin-Inspiron-N5110 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "hannah-admin"

Jul 22 18:34:48 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm:session): session closed for user lightdm

Jul 22 18:34:48 hannahadmin-Inspiron-N5110 lightdm: pam_unix(lightdm:session): session opened for user hannah-admin by (uid=0)

Jul 22 18:34:49 hannahadmin-Inspiron-N5110 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0

Jul 22 18:34:50 hannahadmin-Inspiron-N5110 dbus[939]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.8" (uid=0 pid=1076 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.41" (uid=1000 pid=1677 comm="bluetooth-applet ")

Jul 22 18:34:50 hannahadmin-Inspiron-N5110 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.47 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

Jul 22 18:34:52 hannahadmin-Inspiron-N5110 dbus[939]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.54" (uid=1000 pid=1762 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1269 comm="/usr/sbin/console-kit-daemon --no-daemon ")



Note that I added the  carriage returns in order to improve the readability.

SO, what did she do to the system while she had the administrative password?

TY.

Art

---

