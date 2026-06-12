---
title: "Postgres"
date: 2010-07-25
forum: General Help
---

### Post by Q2299 on 2010-07-25
I am very much interested in Postgres db.
I have installed the DBI and DBD drivers.
Created the Tables.
Can any one help me ..how to access POSTGRES thro a PERL program.
thanks Q2299

---

### Post by EddieO2 on 2010-07-30
Hi,

I have **no** knowledge of PostgreSQL, but if you've got DBD::Pg installed ([http://search.cpan.org/~turnstep/DBD-Pg-2.17.1/Pg.pm](http://search.cpan.org/~turnstep/DBD-Pg-2.17.1/Pg.pm)), you should be able to access the database via DBI as per any database.

Failing that, the Pg module also exists, and may be a simpler interface - see [http://search.cpan.org/~mergl/pgsql_perl5-1.9.0/Pg.pm](http://search.cpan.org/~mergl/pgsql_perl5-1.9.0/Pg.pm)

Cheers,
  EddieO2

---

