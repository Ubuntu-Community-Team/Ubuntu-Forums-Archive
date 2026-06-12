---
title: "System Log Viewer Insists on Opening Non-Existent File"
date: 2012-05-07
forum: General Help
---

### Post by NadirPoint on 2012-05-07
I have been perpetually annoyed by not finding the answer to what must be a common problem since upgrading to squid3 along with 12.04:  The gnome log viewer cannot seem to forget the old squid access.log and dutifully informs me of it's failure to open the non-existent file every time I launch it.  I don't know what's dumber - me for not figuring out this seemingly simple configuration quandary or the apparently brain-dead log viewer.

Anybody else seen this?

---

### Post by dcstar on 2012-05-08
> **NadirPoint said:**
> I have been perpetually annoyed by not finding the answer to what must be a common problem since upgrading to squid3 along with 12.04:  The gnome log viewer cannot seem to forget the old squid access.log and dutifully informs me of it's failure to open the non-existent file every time I launch it.  I don't know what's dumber - me for not figuring out this seemingly simple configuration quandary or the apparently brain-dead log viewer.


Select the file on the LHS and "Close" it.

---

### Post by NadirPoint on 2012-05-08
> **dcstar said:**
> Select the file on the LHS and "Close" it.
I believe it is logically impossible to close a non-existent file that is not already open.

The problem is how to prevent the viewer from attempting to open the non-existent file.

---

### Post by Cheesemill on 2012-05-08
Fire up gconf-editor (you may need to install it first) and edit the /apps/gnome-system-log/logfiles entry.

---

### Post by NadirPoint on 2012-05-08
> **Cheesemill said:**
> Fire up gconf-editor (you may need to install it first) and edit the /apps/gnome-system-log/logfiles entry.
Yaaaaay!!  Thanks for that.  Will try soon as I get home today.  Apart from that one little wrinkle my upgrade to 12.04 went swimmingly...

---

### Post by NadirPoint on 2012-05-08
So 10 hours later, no joy.  Even un-setting the key and logging out has no effect - gnome-system-log continues attempting to open all the same logs, including the old non-existent squid log.

Oddly, run as root, the application loads all the existing logs, does  not return an error for the old squid log, and gconf-editor contains no entry for gnome-system-log.

Do we have a bona-fide bug here?

---

