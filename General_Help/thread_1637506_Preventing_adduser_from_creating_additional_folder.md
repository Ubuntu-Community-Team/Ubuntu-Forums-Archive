---
title: "Preventing adduser from creating additional folders in home directory"
date: 2010-12-04
forum: General Help
---

### Post by armandhr on 2010-12-04
I'm trying to set up a specific directory structure for each home folder whenever I add a new user.  I have what I want in /etc/skel, but I'd also like to eliminate the Documents, Music, Pictures, etc. folders that Ubuntu automatically creates when a new user is added.  Is there any way to do this?  Where are these extra directories defined?  I didn't see anything in the /etc/adduser.conf file--is there some additional script that is run whenever a new user is added?

---

### Post by dcstar on 2010-12-04
> **armandhr said:**
> I'm trying to set up a specific directory structure for each home folder whenever I add a new user.  I have what I want in /etc/skel, but I'd also like to eliminate the Documents, Music, Pictures, etc. folders that Ubuntu automatically creates when a new user is added.  Is there any way to do this?  Where are these extra directories defined?  I didn't see anything in the /etc/adduser.conf file--is there some additional script that is run whenever a new user is added?

AFAIK they are default Gnome folders, automatically created at first login to Gnome by that user. They have nothing to do with the default Linux folders.

---

### Post by armandhr on 2010-12-04
> **dcstar said:**
> AFAIK they are default Gnome folders, automatically created at first login to Gnome by that user. They have nothing to do with the default Linux folders.

Ah, that does make a lot more sense.  So are they set via /etc/xdg or something?  If I set "enabled=False" in /etc/xdg/user-dirs.conf, will that prevent these folders from being generated at the first session, or could I perhaps blank out the entries in /etc/xdg/user-dirs.defaults?

Edit: Marking the thread as solved.  Just in case anyone else has the same question, changing /etc/xdg/user-dirs.conf to "enabled=False" did indeed prevent these folders from being generated at the first login to Gnome.  I am running Ubuntu 10.04.

---

### Post by Tekcronic on 2012-11-29
> **armandhr said:**
> Ah, that does make a lot more sense.  So are they set via /etc/xdg or something?  If I set "enabled=False" in /etc/xdg/user-dirs.conf, will that prevent these folders from being generated at the first session, or could I perhaps blank out the entries in /etc/xdg/user-dirs.defaults?

Edit: Marking the thread as solved.  Just in case anyone else has the same question, changing /etc/xdg/user-dirs.conf to "enabled=False" did indeed prevent these folders from being generated at the first login to Gnome.  I am running Ubuntu 10.04.

As stated in the comments of /etc/xdg/user-dirs.conf

```
# You can also have per-user config in ~/.config/user-dirs.conf, or specify
# the XDG_CONFIG_HOME and/or XDG_CONFIG_DIRS to override this
```
More information can be found here: 
[http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html](http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html)

---

