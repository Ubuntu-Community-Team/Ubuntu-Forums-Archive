---
title: "Can Pam_unix stop booting the auto login system?"
date: 2011-02-21
forum: General Help
---

### Post by Danial on 2011-02-21
Hi, 

Thanks in advance for looking into this question.

I already have two other threads open for a dysfunctional system. 

Thread 1: **Boot hangs at logon sound - no video signal - appears drive is still working** [http://ubuntuforums.org/showthread.php?t=1686554]("http://ubuntuforums.org/showthread.php?t=1686554")

Thread 2: **Where are boot log files and how I can see those?** [http://ubuntuforums.org/showthread.php?t=1692464]("http://ubuntuforums.org/showthread.php?t=1692464")


Basically both of those are for not able to complete the boot (hanging up in the middle of booting) in Karmic.  I had Karmic since it came out but suddenly about two weeks ago just stopped booting.  Except for the battery and resetting BIOS, I had checked all the hardware - and all appear to be okay.  Following a tip from x1a4, I started looking into logs (admittedly not knowing exactly what I am looking for) and I ran into auth.log.  Following is the code.  The highlighted part is confusing (to me) and I am wondering if this may cause to stop booting (or completing the boot process) since I was using auto logon. I do not know if there is anything else (logs) you may need, please advise and I will provide those.

Your help, guidance and **time** is very appreciated.

Danial 

copy of /var/log/auth.log:

```
Feb 14 15:17:01 nix-pc CRON[13251]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 14 15:17:01 nix-pc CRON[13251]: pam_unix(cron:session): session closed for user root
Feb 16 20:03:41 nix-pc gdm-session-worker[1544]: pam_unix(gdm-autologin:session): session opened for user danial by (uid=0)
Feb 16 20:03:41 nix-pc gdm-session-worker[1544]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
[COLOR="DarkRed"]Feb 16 20:03:50 nix-pc gnome-keyring-daemon[1833]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
[/COLOR]Feb 16 20:03:50 nix-pc gnome-keyring-daemon[1833]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Feb 16 20:03:50 nix-pc polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.41 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Feb 20 08:47:43 nix-pc gdm-session-worker[1580]: pam_unix(gdm-autologin:session): session opened for user danial by (uid=0)
Feb 20 08:47:43 nix-pc gdm-session-worker[1580]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Feb 20 08:47:52 nix-pc gnome-keyring-daemon[1843]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Feb 20 08:47:52 nix-pc gnome-keyring-daemon[1843]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Feb 20 08:47:52 nix-pc polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.41 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
[COLOR="DarkRed"]Feb 20 08:56:48 nix-pc gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=danial[/COLOR]
Feb 20 08:56:48 nix-pc gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): getting password (0x00000388)
Feb 20 08:56:48 nix-pc gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): pam_get_item returned a password
[COLOR="DarkRed"]Feb 20 08:56:48 nix-pc gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
[/COLOR]Feb 21 09:53:00 nix-pc gdm-session-worker[1608]: pam_unix(gdm-autologin:session): session opened for user danial by (uid=0)
Feb 21 09:53:00 nix-pc gdm-session-worker[1608]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
```

---

### Post by Danial on 2011-02-22
Well, 

I guess, I have no luck in this situation. :confused:
Thanks for everyone who at least looked into this.

Danial
](*,)

---

