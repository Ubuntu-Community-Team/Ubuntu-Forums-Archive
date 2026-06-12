---
title: "Accidently put updates for unstable firefox releases, now firefox is shizzle"
date: 2010-06-12
forum: General Help
---

### Post by stevevartousky on 2010-06-12
I updated and now I can't save passwords and it deleted all my saved passwords so I tried to get a password manager but then discovered I couldn't get addons. There are many other little errors. Does anybody know how to fix this?:confused:

I am going to put the stable updates on the source.list and take the other out, know what it is?

---

### Post by lovinglinux on 2010-06-12
> **stevevartousky said:**
> I updated and now I can't save passwords and it deleted all my saved passwords so I tried to get a password manager but then discovered I couldn't get addons. There are many other little errors. Does anybody know how to fix this?:confused

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

The files responsible for the passwords are **signons.sqlite** and **key3.db**. If you already lost you passwords, I would recommend deleting those files from your profile.

I also recommend making regular [backups](http://firefox-tutorials.blogspot.com/2010/05/backups.html) and using [Firefox Sync](https://addons.mozilla.org/en-US/firefox/addon/10868/) to avoid loosing your passwords again .

> **stevevartousky said:**
> I am going to put the stable updates on the source.list and take the other out, know what it is?

Disable ubuntu-mozilla-daily or ubuntu-mozilla-security, if present, and then re-install firefox.

---

