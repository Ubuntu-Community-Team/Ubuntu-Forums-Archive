---
title: "postgresql commands from shell"
date: 2010-10-20
forum: General Help
---

### Post by meg23 on 2010-10-20
I built an installation script for ubuntu server that imports postgresql databases automatically. For instance:

sudo su postgres -c 'psql -e template1 < /var/lib/postgresql/everything.sql'

However, when I try to add a user with a password using:

sudo su postgres -c 'psql -e ALTER USER drupal with PASSWORD 'password';'

I get the following:

psql: warning: extra command-line argument "postgres" ignored
psql: warning: extra command-line argument "with" ignored
psql: warning: extra command-line argument "PASSWORD" ignored
psql: warning: extra command-line argument "password" ignored
psql: FATAL:  Ident authentication failed for user "USER"

How can I make this work?

---

