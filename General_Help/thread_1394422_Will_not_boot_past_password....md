---
title: "Will not boot past password..."
date: 2010-01-30
forum: General Help
---

### Post by panamacmillan on 2010-01-30
Hi all...As a relative newbie to Ubuntu(Linux in general),I have this problem where my computer boots past password then sits there.
    I believe some 'Up-dates' had preceded this event.
Any tips on what to do...please ...
    Thanks for your time.

---

### Post by cariboo on 2010-01-30
Start in recovery mode, when you get to the menu select drop to root prompt, using the arrow keys. At the prompt type:

```
apt-get -f install
```

to see if it installs any missing dependencies. If that doesn't work try doing an update:

```
aptitude update && aptitude safe-upgrade
```

once either of the above commands finish, type:

```
exit
```

then once at the menu select resume.

---

