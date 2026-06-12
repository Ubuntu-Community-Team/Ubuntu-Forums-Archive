---
title: "PostgreSQL install error"
date: 2011-04-24
forum: General Help
---

### Post by siucdude on 2011-04-24
Well I don't usually get to post alot but here is a weird one!!
I burned 9.10 10.04, 10.10 and 11.04 server i386 cd, 
Then on first install I did with no packages
And second install I did with OpenSSH Server and PostgreSQL Server,

Each time I get PostgresSQL error after 

see below, I tried to google and looks like this is a one in a million error. I do a simple apt-get install and then I get error to run pg_createcluster 8.4 main --start, what is weird is that I have 2 servers and they have no errors, it seems like this one new server is giving me a run for its money. 
Has anyone ever heard for a package not to install because of hardware? I mean level of package like this one.

[I]root@server1:/home/me# pg_createcluster 8.4 main --start
Creating new cluster (configuration: /etc/postgresql/8.4/main, data: /var/lib/postgresql/8.4/main)...
FATAL:  invalid restriction selectivity: 1.000000
STATEMENT:  UPDATE pg_database SET      datistemplate = 't',    datallowconn = 'f'     WHERE datname = 'template0';

child process exited with exit code 1
initdb: removing contents of data directory "/var/lib/postgresql/8.4/main"
Error: initdb failed[/I]

---

