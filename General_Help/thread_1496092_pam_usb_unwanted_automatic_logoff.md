---
title: "pam_usb unwanted automatic logoff"
date: 2010-05-28
forum: General Help
---

### Post by dschep on 2010-05-28
I've setup pam_usb to allow me to log in with just my usb drive. This works fine, save for one issue. When I log in using pam_usb, my session dies abruptly if I unplug the usb drive. I am _not_ runing pamusb-agent.

It seems like there may be some issue with policykit, but I'm not sure.

/var/log/auth.log:
```
May 28 20:42:10 nitrogen gdm-session-worker[1836]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dschep"
May 28 20:42:10 nitrogen pam_usb[1836]: pam_usb v0.4.2
May 28 20:42:10 nitrogen pam_usb[1836]: Authentication request for user "dschep" (gdm)
May 28 20:42:10 nitrogen pam_usb[1836]: Device "iamakey" is connected (good).
May 28 20:42:10 nitrogen pam_usb[1836]: Performing one time pad verification...
May 28 20:42:11 nitrogen pam_usb[1836]: Access granted.
May 28 20:42:11 nitrogen gdm-session-worker[1836]: pam_unix(gdm:session): session opened for user dschep by (uid=0)
May 28 20:42:11 nitrogen gdm-session-worker[1836]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 28 20:42:11 nitrogen gnome-keyring-daemon[1967]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified#012Autolaunch error: X11 initialization failed.
May 28 20:42:11 nitrogen gnome-keyring-daemon[1967]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
May 28 20:42:12 nitrogen gnome-keyring-daemon[1967]: The SSH agent was already initialized
May 28 20:42:12 nitrogen gnome-keyring-daemon[1967]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
May 28 20:42:13 nitrogen polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.34 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
May 28 20:42:32 nitrogen polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.34, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)

```

/etc/pam.d/common-auth:
```
auth  sufficient          pam_usb.so allow_remote=1

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]  pam_unix.so nullok_secure
auth    [success=1 default=ignore]  pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite           pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

EDIT: It even seems to kill my session when I've logged in with the password, then insert the usb drive.

---

### Post by ifail on 2010-06-22
Bump. I am interested about this as well.

---

### Post by jouva on 2010-12-01
If you're still having issues with logging out and X sessions, it's related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451](https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451)

The gdm sessions is crashing due to hal crashing, so it's not so much a "logout" so much as it is a crash.

---

