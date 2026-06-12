---
title: "Updating Bugzilla"
date: 2006-05-08
forum: General Help
---

### Post by pascal_belron on 2006-05-08
I installed ubuntu 5.10 here at work on an old server to demonstrate capabilities of bugzilla. I m in charge of a dev team and I d like my team and some power users in the company to use bugzilla. I installed the stock bugzilla that comes with breezy (2.18.xxx) and a skin I found on the net to make things prettier.

Now I d like to update to the last bugzilla release (2.22.0). Thing is that ubuntu uses a non standard bugzilla installation (split in 3 directories). So I can t just do a stock upgrade from the tarball. Does anyone know if this has been covered already ? I looked on the forums and tried to google it, but to no avail.

If anyone has performed the same upgarde, I d like to hear from your experience. Otherwise I ll try manually to sort out the files from the tarball in the 3 directories ubuntu uses for bugzilla.

---

### Post by marko on 2006-05-10
I am in your boat.  ](*,)  Am also trying to do this upgrade as well, but a little different.  Have a bugzilla .18 installed on a RH machine.  Want to take a .tgz of that db, move it over to a working .20 bugzilla setup on Dapper.

My problem with the odd setup in Ubuntu is where to put this .18 database..  I have tried /var/lib/mysql/bugzilla to no success.  Found that if I drop the bugzilla db, and put the .18 database in /var/lib/mysql/bugs/, checksetup.pl will create a new blank /var/lib/mysql/bugzilla db.  But, I don't want a blank db, I want my .18 db upgraded to .20..

:confused: 

Maybe someone will chime in and tell us where to put the older copy of .18 db so that checksetup.pl will correctly upgrade it for .20+ to use.

(I hate looking for help on Bugzilla.  It is like searching for your lost friend Joe.  Too many many hits that are bogus..)

---

### Post by marko on 2006-05-23
i tried to give notes on getting this accomplished.  the entry screen timed out on me and wiped my efforts.  if you are really interested, send me a note.  otherwise, i am bailing on this forum for now.

---

