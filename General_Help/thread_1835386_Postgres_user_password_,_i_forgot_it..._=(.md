---
title: "Postgres user password , i forgot it... =("
date: 2011-08-29
forum: General Help
---

### Post by DaH-RaT on 2011-08-29
Forgot Postgres password help :(
i havent used my postgres in a while and ended up needing to but forgot my pass.

xx@ubuntu:~$ su postgres -c psql
Password:
su: Autherntication Failure

this is my user account(postgres) on the postgresql that is passworded.

ive attempted to change the pg_hba.conf to trust on the local unix area, restarted the service but it still asks me for a password... any ideas?

---

