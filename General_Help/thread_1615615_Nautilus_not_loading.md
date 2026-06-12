---
title: "Nautilus not loading"
date: 2010-11-07
forum: General Help
---

### Post by ATMarsden on 2010-11-07
I've been using Linux Ubuntu for about 2 months now, and this is an interesting error...

Anyone know how to fix it?

When I loaded up the past two times, I've had issues...

I get the following series of message:

> Could not update ICEauthority file /home/atmarsden.ICEauthority

There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

**Nautilus could not create the following required folders: /home/atmarsden/desktop, /home/atmarsden/nautilus.**
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

Followed by a blank screen with just my background... screensavers worketh not, and Alt-F2 only seems to run terminal, no apps.

Running an example app in terminal (Chrome):

```
atmarsden@ATMarsden-Acer:~$google-chrome
[1874:1874:900308257:FATAL:chrome/browser/browser_main.cc(881)] Check failed: PathService::Get(chrome::DIR_USER_DATA, &user_data_dir). Must be able to get user data directory!
Aborted
atmarsden@ATMarsden-Acer:~$|
```

So, any ideas on getting this working again?

---

### Post by stuarttanner on 2010-11-07
have you tryed typeing sudo nautilus in the terminal will that open nautilus

---

