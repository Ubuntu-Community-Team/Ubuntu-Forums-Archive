---
title: "raid like multiple computers mirrored data"
date: 2011-06-21
forum: General Help
---

### Post by Cool Javelin on 2011-06-21
This has probably been answered before, but I don't know how to form the search to find out...

I would like to have redundant data and backups folders on multiple Ubuntu servers.

I would like this to be transparent so when I read a file, I get it from only one server, but when I write it goes to both.

Ideally, it would write to both machines simultaneously. Further, it would be nice if the data were transmitted from my other workstations only once over the network to minimize file write time. Failing that, send the data from a "primary" backup to a "secondary" backup after the fact but more slowly to minimize network congestion.

We recently had a power failure here and it hosed one of my servers that had my backups (I know, I know, I need more UPS's.) Fortunatly 3 of the 4 drives survived and I only lost the OS, not my backups, but it made me want a more robust backup system.

The only way I can think is to actually have multiple machines with redundant data (not to hard, I have accumulated a lot of hard drives over the years.)

Any ideas and links to how to websites would be very helpful.

Thanks,
Mark.

---

### Post by psusi on 2011-06-21
Setup a cron job to rsync every 5 minutes.

---

