---
title: "Mediawiki installation help!"
date: 2009-11-03
forum: General Help
---

### Post by truKrewl on 2009-11-03
Hello all

I have been trying to install mediawiki (1.11.2 - yes I know its an old version but this way I get to test upgrades out as well :) ) using postgresql (8.3) but I am running into problems after the configuration.

Error:-

# Database type: PostgreSQL
# Loading class: DatabasePostgres
# Attempting to connect to database "postgres" as superuser "postgres"...
# Checking the version of Postgres...version 8.3 is OK.
# User "wikiuser" already exists, skipping account creation.
# Database "wikidb" already exists, skipping database creation.
# Connecting to "wikidb" as superuser "postgres" to check rights...OK
# Checking that tsearch2 is installed in the database "wikidb"...FAILED. tsearch2 must be installed in the database "wikidb".

I followed the installation manual on the mediawiki so thought I had done this - when I look at the wikidb I see a trigger function called tsearch2...what have i missed??? 

Thanks

tru.

---

