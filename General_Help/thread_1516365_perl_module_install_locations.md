---
title: "perl module install locations"
date: 2010-06-23
forum: General Help
---

### Post by five0.4tluv on 2010-06-23
First, I apologize if this is the wrong forum

I'm having a bit of an issue with existing scripts (from FreeBSD hosts) that I am wanting to move over to Ubuntu 10.04 LTS Server 64bit. Specifically for now I'm working on getting scripts to run that need DBI and mysql. I install libdbd-mysql-perl using apt-get. I really don't want to add any additional library paths to @INC during runtime or by rebuilding perl with them in, I'd like to always be able to just use perl default @INC so I can move to any OS.

libdbd-mysql-perl modules are located in

/usr/lib/perl5/Bundle/DBD/mysql.pm
/usr/lib/perl5/DBD/mysql.pm

perl -e "print join(\"\n\", @INC);"

/etc/perl
/usr/local/lib/perl/5.10.1
/usr/local/share/perl/5.10.1
/usr/lib/perl5
/usr/share/perl5
/usr/lib/perl/5.10
/usr/share/perl/5.10
/usr/local/lib/site_perl

If anyone can give me any suggestions I would appreciate it.

---

