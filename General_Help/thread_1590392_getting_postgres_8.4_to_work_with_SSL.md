---
title: "getting postgres 8.4 to work with SSL?"
date: 2010-10-07
forum: General Help
---

### Post by digitalramble on 2010-10-07
Hi, all.  I'm running a postgres 8.4 server on my Ubuntu 10.4 (64 bit) install and having some trouble getting the SSL to run.

Here is what I have done so far.

Postgres has been compiled with SSL turned on.

postgresql.conf has listen_addresses = '*'
the tcpip_socket = true does not appear to be recognized in this version?
I had to comment it out, since server restart always complains about unrecognized parameter.

pg_hba.conf has
hostssl all     all     xxx.xxx.xxx.0/24        cert

as the very last line.  (I have some previous lines with ident, but since I am not running identd they will not come into play)

I created a server.key and server.crt as per the instructions over at Postgres documentation.  I also created client certificates (much more difficult to do as there's no documentation and I finally just played around with openssl's documentation and such.  These are properly placed in the client's ~/.postgresql directory as postgresql.key & crt


Now this is what I find.  If I replace the last line in pg_hba.conf above with trust instead of cert, I can connect to the postgres server (using psql) and there's a line that says:
SSL connection (cipher: DHE-RSA-AES256-SHA, bits: 256)


hmmm...

if I change that trust to cert, I get:

psql: FATAL:  no pg_hba.conf entry for host "xxx.xxx.xxx.y", user "xxx", database "xxx", SSL off


I have gone around and around on this and would appreciate any ideas or thoughts about this??

Thanks,
--Cindy

---

