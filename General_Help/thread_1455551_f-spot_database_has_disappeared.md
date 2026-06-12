---
title: "f-spot database has disappeared"
date: 2010-04-16
forum: General Help
---

### Post by rinrada on 2010-04-16
When I opened F-spot this morning I got an error message, then it opened a new database - which has nothing in it.:sad: Reopening f-spot simply loads the new empty database again.:sad::sad:

Can anybody help me find my old database and get f-spot to use it again?

The new database appears to be located in ~/.config/f-spot/photos.db (I'll print out the contents below).

Thanks.

BEGIN TRANSACTION;
CREATE TABLE photos (
    id            INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, 
    time            INTEGER NOT NULL, 
    base_uri        STRING NOT NULL, 
    filename        STRING NOT NULL, 
    description        TEXT NOT NULL, 
    roll_id            INTEGER NOT NULL, 
    default_version_id    INTEGER NOT NULL, 
    rating            INTEGER NULL, 
    md5_sum            TEXT NULL
);
CREATE INDEX idx_photos_roll_id ON photos(roll_id);
COMMIT;

---

### Post by GeoffAk on 2010-07-21
I'm having the exact same problem.  The error message said where the F-spot database is located, but I didn't think to write it down.  Anyone know where to find it?

---

### Post by mike555 on 2010-07-21
if you get tired of f-spot , shotwell is very good ..

---

### Post by GeoffAk on 2010-07-22
I found it.  F-spot moves the database to the home folder under /home/<username>.  Hope this helps anyone else with this problem.

---

### Post by JanneM on 2010-08-01
Ah, thanks. I got hit by the same bug.

BTW, Shotwell is not a realistic replacement for F-spot. It doesn't seem to be able to store and handle several versions of the same image. It doesn't handle large number of tags in any sensible manner (hierarchical tags, for instance, where adding one tag will add the parent tags). Probably OK for handling smaller number of images where you don't actually want to do much with them, but not for large numbers, when you most need organizing.

---

