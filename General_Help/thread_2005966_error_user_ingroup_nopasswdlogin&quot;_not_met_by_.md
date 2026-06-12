---
title: "error? user ingroup nopasswdlogin&quot; not met by user"
date: 2012-06-18
forum: General Help
---

### Post by oklokl on 2012-06-18
no autoloing
Auto-login account, not a ...
However, the following message is output.
Is it normal output message?

# who  
ukuk   pts/1        2012-06-19 02:38 (:0)



Linux ubuntu 3.4.0-5-generic #11~precise1-Ubuntu SMP Wed Jun 6 01:55:41 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

[COLOR=Red]pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0[/COLOR]
[COLOR=Red]requirement "user ingroup nopasswdlogin" not met by user "ukuk"[/COLOR]

[COLOR=Red]Jun 19 02:26:44 kde dbus[644]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.23" (uid=104 pid=1673 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0"[/COLOR]



syslog
Jun 19 02:16:51 kde sudo: pam_unix(sudo:session): session closed for user root
Jun 19 02:19:02 kde polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.45, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale ko_KR.UTF-8) (disconnected from bus)
Jun 19 02:26:42 kde lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jun 19 02:26:42 kde lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jun 19 02:26:43 kde lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ukuk"
Jun 19 02:26:44 kde dbus[644]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.23" (uid=104 pid=1673 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1399 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jun 19 02:26:54 kde lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jun 19 02:26:54 kde lightdm: pam_unix(lightdm:session): session opened for user ukuk by (uid=0)
Jun 19 02:26:54 kde lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jun 19 02:26:56 kde gnome-keyring-daemon[1750]: failed to unlock login keyring on startup
Jun 19 02:26:57 kde polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.44 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale ko_KR.UTF-8)
Jun 19 02:27:02 kde dbus[644]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=2088 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1399 comm="/usr/sbin/console-kit-daemon --no-daemon ")

---

