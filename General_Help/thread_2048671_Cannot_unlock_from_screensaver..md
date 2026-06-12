---
title: "Cannot unlock from screensaver."
date: 2012-08-27
forum: General Help
---

### Post by cmani on 2012-08-27
Hi All,

One of my ubuntu desktop can't unlock from screen saver.

They /var/log/auth.log is as below


Aug 27 15:52:19 linux-mchandra dbus[729]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.160" (uid=104 pid=832 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1086 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Aug 27 15:52:20 linux-mchandra dbus[729]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.168" (uid=104 pid=880 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1086 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Aug 27 15:52:23 linux-mchandra lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=cmani
Aug 27 15:52:23 linux-mchandra lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
Aug 27 15:52:23 linux-mchandra lightdm: pam_winbind(lightdm:auth): pam_get_item returned a password
Aug 27 15:52:23 linux-mchandra lightdm: pam_winbind(lightdm:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug 27 15:52:26 linux-mchandra lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "cmani"

Always i force to use "switch user" option than "Unlock Option".  Pl. advice me to this prob fixed.

---

