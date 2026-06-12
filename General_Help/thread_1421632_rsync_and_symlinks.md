---
title: "rsync and symlinks"
date: 2010-03-04
forum: General Help
---

### Post by tpmoney on 2010-03-04
I have a postgresql installation that is using table spaces. As a result every table space exists as follows:

/pgdata/tablespace1
/pgdata/tablespace2

In addition, postgresql has a tablespace directory with symlinks that point to these tablespaces as follows:

/pgdata/pg_tblspc/27893 -> /pgdata/tablespace1
/pgdata/pg_tblspc/9802 -> /pgdata/tablespace2

I have a second machine that is going to act as a backup of sorts. Postgres can be backed up with rsync no problem, however, I don't want to rsync the entire /pgdata directory as it contains some machine specific information as well.

What I would like to do is be able to rsync the pg_tblspc directory, and have rsync copy the sym links and the linked directories to the remote machine, and create any /pgdata/tablespace* directories as needed, so that I don't have to worry about adding a new rsync command every time I create a new tablespace.

So instead of a script that does:
rsync /pgdata/tablespace1 ...
rsync /pgdata/tablespace2 ...
rsync /pgdata/pg_tblspc ...

I would just like to be able to run:

rsync /pgdata/pg_tblspc

I've been bouncing off this for a while and unfortunately, I can't seem to figure out the right combination of options that will both preserve the symlinks, and copy the linked directories and files to their appropriate locations.

EDIT:
---------

I tried doing an rsync --include="*/" --exclude="*" since what I'm concerned with copying are directories (and their contained files) but that appeared to only copy the directories and not the files within them.

---

### Post by psusi on 2010-03-04
I'd say rsync the symlinks first, then go back and get what they point to with something like this:

find -type l -print0 | xargs -0 readlink | xargs -I {} rsync {} destination

---

### Post by tpmoney on 2010-03-04
Will that also handle the creation of new table spaces without having to explicitly create the new table space in the destination? So for example:

```

BEFORE RSYNC AND FIND SCRIPT
source:
/pgdata/pg_tblspc/456 -> /pgdata/tablespace1/
/pgdata/pg_tblspc/4331 -> /pgdata/tablespace2/
/pgdata/pg_tblspc/6543 -> /pgdata/tablespace3/
/pgdata/tablespace1/
/pgdata/tablespace2/
/pgdata/tablespace3/

destination:
/pgdata/pg_tblspc/456 -> /pgdata/tablespace1/
/pgdata/pg_tblspc/4331 -> /pgdata/tablespace2/
/pgdata/tablespace1/
/pgdata/tablespace2/

``````

AFTER RSYNC BEFORE FIND SCRIPT

destination:
/pgdata/pg_tblspc/456 -> /pgdata/tablespace1/
/pgdata/pg_tblspc/4331 -> /pgdata/tablespace2/
/pgdata/pg_tblspc/6543 -> /pgdata/tablespace3/
/pgdata/tablespace1/
/pgdata/tablespace2/

``````

AFTER RSYNC AND FIND SCRIPT
  
destination:
/pgdata/pg_tblspc/456 -> /pgdata/tablespace1/
/pgdata/pg_tblspc/4331 -> /pgdata/tablespace2/
/pgdata/pg_tblspc/6543 -> /pgdata/tablespace3/
/pgdata/tablespace1/
/pgdata/tablespace2/
/pgdata/tablespace3/
 
```

---

