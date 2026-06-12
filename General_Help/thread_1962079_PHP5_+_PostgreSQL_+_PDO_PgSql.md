---
title: "PHP5 + PostgreSQL + PDO_PgSql"
date: 2012-04-20
forum: General Help
---

### Post by Krylovech on 2012-04-20
Hello.

I have to install on two clean machines following things:
On the first one - database (PgSql);
On the second one - php + apache2 + pdo (LAN connecting to DB).
Without unnecessary packages.

I can't google detailed installation, only articles like "Just Let It Work"..
So, which packages (list of pack. names) I have to install on the first machine & second one? I hope you'll help..

On the second, I know only that I'll install apache2 & php5 packages. :)

Thank you.

---

### Post by SeijiSensei on 2012-04-20
On the server you should just need postgresql (the server) and postgresql-client.  

If you prefer, you can install the more recent version, postgresql-9.1 and postgresql-client-9.1.  These are both available in the repositories for my 12.04 development release; the actual release date for Precise is about a week from now.  I don't see much reason not to install 12.04 now as long as you update the packages routinely.  On servers you want to use "LTS" versions, and the last such version, 10.04, is two years old now. If you're comfortable at the command line, or expect to manage the system remotely via SSH, I'd use the [server version]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/") of Ubuntu.

On the Apache machine, make sure you install the php5-pgsql package as well.  That contains the PHP modules that implement the various [PG functions]("http://www.php.net/manual/en/book.pgsql.php").  If you're only communicating from PHP to Postgresql, I don't see any reason to go the pdo route unless you're more comfortable with it.  If you have to make queries against a variety of different types of databases, the pdo interface has merit.  I've written PHP/PostgreSQL applications for many years now and never used pdo.

---

