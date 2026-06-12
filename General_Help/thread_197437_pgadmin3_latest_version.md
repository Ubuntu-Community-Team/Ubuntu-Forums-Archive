---
title: "pgadmin3 latest version"
date: 2006-06-15
forum: General Help
---

### Post by jlintz on 2006-06-15
Anyone know where I can get a deb for the latest pgadmin3.  I noticed the latest version in dapper is quite old and I'm having a hefty time trying to compile it from source

---

### Post by jlintz on 2006-06-15
nm, found a respository here for anyone else who needs the latest version

deb [ftp://ftp2.us.postgresql.org/postgresql/pgadmin3/release/debian](ftp://ftp2.us.postgresql.org/postgresql/pgadmin3/release/debian) stable pgadmin

add that to your /etc/apt/sources.list and then sudo apt-get update && sudo apt-get upgrade and it worked.

---

