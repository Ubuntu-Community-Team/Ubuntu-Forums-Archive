---
title: "Ubuntu Session ends abruptly"
date: 2011-06-09
forum: General Help
---

### Post by rereradu on 2011-06-09
Hey guys!
Here's my problem: from time to time (once every few days) my session ends out of the blue. I get logged out as if I was doing a manual log out. This happens quite rare (once a week maybe), but after ignoring it for the first few times I decided this is an issue I should deal with. 
The session ends when doing different things (last time, just a few minutes ago, I had PlayOnLinux running and had just clicked on the Install button. Sometimes I'm just browsing, and once it even happened while I was doing nothing at all). 

Here's the information from the auth.log from the exact time when it happened:
```

Jun  9 19:49:28 silverbox polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.18, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Jun  9 19:49:29 silverbox gnome-keyring-daemon[1236]: dbus failure unregistering from session: Connection is closed
Jun  9 19:49:29 silverbox gnome-keyring-daemon[1236]: dbus failure unregistering from session: Connection is closed
Jun  9 19:49:29 silverbox gdm-session-worker[1154]: pam_unix(gdm-autologin:session): session closed for user radu
Jun  9 19:49:38 silverbox gdm-session-worker[11594]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "radu"
Jun  9 19:49:41 silverbox gdm-session-worker[11594]: pam_unix(gdm:session): session opened for user radu by (uid=0)
Jun  9 19:49:41 silverbox gdm-session-worker[11594]: pam_ck_connecto Unregistered Authentication Agent for unix-sessionr(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jun  9 19:49:46 silverbox polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.78 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jun  9 19:49:51 silverbox pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Jun  9 19:49:51 silverbox pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Jun  9 19:49:51 silverbox pkexec[12341]: radu: Executing command [USER=root] [TTY=unknown] [CWD=/home/radu] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 2]
Jun  9 19:49:51 silverbox dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.86" (uid=1000 pid=12068 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=798 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Jun  9 19:49:57 silverbox dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.89" (uid=1000 pid=12634 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=798 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Jun  9 19:49:58 silverbox pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Jun  9 19:49:58 silverbox pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Jun  9 19:49:58 silverbox pkexec[12726]: radu: Executing command [USER=root] [TTY=unknown] [CWD=/home/radu] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 7]

```I am kind of worried about the first line. 
What does it mean?

```
silverbox polkitd(authority=local):** Unregistered Authentication Agent for unix-session**:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.18, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
```I'm a bit worried for the security of my PC. Is this a hack? Is it a hardware failure? Where else should I look for more information on finding the cause of these abrupt log-outs? What other logs can give me this useful information?

Thx,
Radu

---

### Post by nwilson5 on 2012-04-27
I'm having the same issue. I'm on the beta version of 12.04 and it was just released so I'm going to upgrade and see if it fixes it.

Just started searching around about this, as I saw that same thing in my auth.logs.

---

