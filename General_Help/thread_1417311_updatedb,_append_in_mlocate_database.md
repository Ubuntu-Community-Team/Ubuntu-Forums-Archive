---
title: "updatedb, append in mlocate database"
date: 2010-02-27
forum: General Help
---

### Post by jobano on 2010-02-27
Hi,

I was wondering finding a way to partially update the mlocate.db but as far as I'm looking for, this is not possible.

What I would like to do:
[LIST]
[*]Daily: Let the system normally update the database according to the main configuration file, but pruning the update of a directory (/media/ExtUsbDrive) _without erasing its content !_
[*]Sometimes, when plugging in my external drive: Update that directory only (/media/ExtUsbDrive) _without erasing the whole rest of the system files listing_.
[/LIST]

Hope I do make sens.

As far as that kind of pruning is apparently not directly possible with updatedb, I was thinking about a different mlocate.db file for my external drive, that could be appended to the main one after each daily update...

Cheers

---

