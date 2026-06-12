---
title: "Problems reinstalling postgresql"
date: 2006-02-21
forum: General Help
---

### Post by shartrec on 2006-02-21
I have being trying to reinstall Postgresql and it doesn't work.  I previously had Postgresql 8.0 installed on Ubuntu 5.10 but removed it ( don't ask why, obviously not a good idea) now I want to reinstall, but  it doesn't.

I tried installing with both apt-get and synaptic.  Used the following with  apt
[FONT="Courier New"] sudo apt-get install postgresql-8.0 postgresql-client-8.0[/FONT]

There are no errors reported but the server just doesn't start.

I tried running [FONT="Courier New"]sudo /etc/init.d/postgresql-8.0 start[/FONT] but nothing started.

I just get the following error when I try to do anything.

[FONT="Courier New"]createdb: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
[/FONT]

There doesn't seem to be any config or data files anywhere on the system.  Not that I can find anyway.  I have tried uninstalling and reinstalling many times but with no luck

---

