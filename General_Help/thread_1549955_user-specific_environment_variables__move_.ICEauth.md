---
title: "user-specific environment variables / move .ICEauthority for multiple users"
date: 2010-08-10
forum: General Help
---

### Post by Interruptor on 2010-08-10
I'm searching a way to set environment variables after $HOME was set and before *iceauth* start.
The problem is .ICEauthority file which I want to move somewhere from *~*
Final goal is to restrict a couple of users to write to their home directories. I think it can be called kiosk mode.
I already found out that the whole ***~*** tree can be locked down (either by *chown* or *chattr*) almost without problems.
.ICEauthority is final problem, which has to be written every login, but is restricted even if it's link (either symbolic or hard) to writeable location.
**ICEAUTHORITY** variable can control it's location and now I'm stuck trying to make it user-specific (one file even with number-of-the-beast 777 privileges gets locked by first logged-in user).
Neither in */etc/environment* or in */etc/gdm/PreSession/Default* it refuses to recognise $HOME: it's stored as "$HOME" exactly, not as "/home/user".

Any ideas?
I've tried:
```
export ICEAUTHORITY=/.authorities$HOME.ICEauthority
export ICEAUTHORITY="/.authorities"$HOME".ICEauthority"
```

**UPD**:
*~/.bashrc* is too late.
Now I stopped trying to export environment variable for other user. (to put that line in **/etc/gdm/PostLogin/Default**)
*sudo -u username ./bashscript*
seems to export variable not to username environment...

---

