---
title: "Command to determine active user (Not $USER varible)"
date: 2010-07-21
forum: General Help
---

### Post by undecim on 2010-07-21
I'm trying to write a small script that will run as root, but launch a command with sudo as another user. I want that user to be whichever user is active user. That is, the user that is using GDM right now, or the one that is logged into the current console. (by current console, I don't mean the user running the script, but rather the user logged into the console currently displayed on the screen.)

How can this be done?

```
ACTIVE_USER=`somecommand`
test `id -u pulse` -ge 1000 && sudo -u $ACTIVE_USER $*
```

What can I use for "somecommand"?

---

### Post by dcstar on 2010-07-21
> **undecim said:**
> I'm trying to write a small script that will run as root, but launch a command with sudo as another user. I want that user to be whichever user is active user. That is, the user that is using GDM right now, or the one that is logged into the current console. (by current console, I don't mean the user running the script, but rather the user logged into the console currently displayed on the screen.)

How can this be done?

```
ACTIVE_USER=`somecommand`
test `id -u pulse` -ge 1000 && sudo -u $ACTIVE_USER $*
```

What can I use for "somecommand"?

The commands **w** and **who** will show you who is logged in to what.

---

### Post by undecim on 2010-07-21
> **dcstar said:**
> The commands **w** and **who** will show you who is logged in to what.

That doesn't tell me who the active user is. I suppose that I could use information from that if I could tell what the active console is.

---

### Post by aphatak on 2010-07-21
The command 'whoami' should tell you who you have logged in as in the current session.

---

### Post by undecim on 2010-07-21
> **aphatak said:**
> The command 'whoami' should tell you who you have logged in as in the current session.

"whoami" will always be root in this case because the script is run as root. That is not what I want.

---

### Post by rubylaser on 2010-07-21
I'm not sure if this is what you mean, but this will retrieve the most current person using GDM
```
ps aux | grep gdm | tail -n 1 | cut -d ' ' -f 1
```

Probably a much better way to do this, but this might work for you.

---

