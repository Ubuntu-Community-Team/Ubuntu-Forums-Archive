---
title: "Default language for each user"
date: 2010-05-20
forum: General Help
---

### Post by mghis on 2010-05-20
I have to set a default language for each user.
Example: in my system there are the following users

usera, userb

How can i set 'English' for userb, and 'French' for userb?

It may be a stupid question but I'm a newbie...


Thanks for any help! :)

---

### Post by angry_johnnie on 2010-05-20
install the desired language pack

upon the next login, look at the bottom panel.  there is a language box.  choose desired language.  it will be remembered next time that user logs in.

---

### Post by mghis on 2010-05-20
> **angry_johnnie said:**
> install the desired language pack

upon the next login, look at the bottom panel.  there is a language box.  choose desired language.  it will be remembered next time that user logs in.

That works with the gdm.
The user is connected by a serial terminal.

I followed your instructions but if I login by a tty and not by the GDM, it don't work.

Thanks for any further answer! :)

---

### Post by mghis on 2010-05-20
SOLVED!!! :D :D ;)

Csh, tcsh et similia:
```
setenv LANG en_DE-UTF-8
```

Sh, Ksh, bash:
```
export ---etc---
```


Thanks for the promptly answers!

---

