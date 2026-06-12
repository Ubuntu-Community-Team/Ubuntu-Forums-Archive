---
title: "KDE/KDM and Gnome-Keyring"
date: 2011-07-27
forum: General Help
---

### Post by BrantlyMedders on 2011-07-27
Greetings all,

I'm having an issue with KDE and gnome-keyring.  I use KDE as my main desktop environment, but there are a few GNOME apps I would like to use that rely upon gnome-keyring (Ubuntu One being a prime example).

I would like my default keyring to unlock whenever I log in to KDE (as it does in Gnome).

I've read a few tutorials online, but none of them seem to work properly.  All of them revolve around adding the following two lines to /etc/pam.d/kdm

```

auth    optional pam_gnome_keyring.so try_first_pass
session optional pam_gnome_keyring.so autostart

```

For reference, here's the entirety of my /etc/pam.d/kdm file:
```

auth       required     pam_nologin.so
auth       required     pam_env.so readenv=1
auth       required     pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth 	optional pam_gnome_keyring.so try_first_pass
session    required     pam_limits.so
@include common-account
@include common-password
@include common-session

session optional pam_gnome_keyring.so autostart

```

---

