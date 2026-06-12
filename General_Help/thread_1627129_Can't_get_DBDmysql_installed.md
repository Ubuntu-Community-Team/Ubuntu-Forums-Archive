---
title: "Can't get DBD::mysql installed"
date: 2010-11-21
forum: General Help
---

### Post by mindlessbrain on 2010-11-21
**Hello all,**

**I definitely don't have mysql installed. (Just to check)** 

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# mysql
The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1
Try: apt-get install <selected package>

[B]I can download the first two, but it won't let me download the last one through apt-get install.
  
If I try and install it through cpan I get:[/B]

cpan[6]> install DBD::mysql
Running install for module 'DBD::mysql'
Running make for C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz
  Has already been unwrapped into directory /root/.cpan/build/DBD-mysql-4.018-SIgigK
  '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512, won't make
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install

cpan[1]> force install DBD::mysql
CPAN: Storable loaded ok (v2.20)
Going to read '/root/.cpan/Metadata'
  Database was generated on Sun, 21 Nov 2010 07:42:41 GMT
Running install for module 'DBD::mysql'
CPAN: YAML loaded ok (v0.72)
Running make for C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz
CPAN: Digest::SHA loaded ok (v5.48)
CPAN: Compress::Zlib loaded ok (v2.03)
Checksum for /root/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz ok
Scanning cache /root/.cpan/build for sizes
............................................................................DONE
CPAN: Archive::Tar loaded ok (v1.72)
DBD-mysql-4.018/
DBD-mysql-4.018/ChangeLog
DBD-mysql-4.018/constants.h
DBD-mysql-4.018/dbdimp.c
DBD-mysql-4.018/dbdimp.h
DBD-mysql-4.018/eg/
DBD-mysql-4.018/eg/bug14979.pl
DBD-mysql-4.018/eg/bug21028.pl
DBD-mysql-4.018/eg/bug30033.pl
DBD-mysql-4.018/eg/bug30033pg.pl
DBD-mysql-4.018/eg/decimal_test.pl
DBD-mysql-4.018/eg/issue21946.pl
DBD-mysql-4.018/eg/prepare_memory_usage.pl
DBD-mysql-4.018/eg/proc_example1.pl
DBD-mysql-4.018/eg/proc_example2.pl
DBD-mysql-4.018/eg/proc_example2a.pl
DBD-mysql-4.018/eg/proc_example2b.pl
DBD-mysql-4.018/eg/proc_example3.pl
DBD-mysql-4.018/eg/proc_example4.pl
DBD-mysql-4.018/INSTALL.html
DBD-mysql-4.018/lib/
DBD-mysql-4.018/lib/Bundle/
DBD-mysql-4.018/lib/Bundle/DBD/
DBD-mysql-4.018/lib/Bundle/DBD/mysql.pm
DBD-mysql-4.018/lib/DBD/
DBD-mysql-4.018/lib/DBD/mysql/
DBD-mysql-4.018/lib/DBD/mysql/GetInfo.pm
DBD-mysql-4.018/lib/DBD/mysql/INSTALL.pod
DBD-mysql-4.018/lib/DBD/mysql.pm
DBD-mysql-4.018/Makefile.PL
DBD-mysql-4.018/Makefile.PL.embedded
DBD-mysql-4.018/MANIFEST
DBD-mysql-4.018/MANIFEST.SKIP
DBD-mysql-4.018/META.yml
DBD-mysql-4.018/myld
DBD-mysql-4.018/mysql.xs
DBD-mysql-4.018/README
DBD-mysql-4.018/t/
DBD-mysql-4.018/t/00base.t
DBD-mysql-4.018/t/10connect.t
DBD-mysql-4.018/t/20createdrop.t
DBD-mysql-4.018/t/25lockunlock.t
DBD-mysql-4.018/t/29warnings.t
DBD-mysql-4.018/t/30insertfetch.t
DBD-mysql-4.018/t/31insertid.t
DBD-mysql-4.018/t/32insert_error.t
DBD-mysql-4.018/t/35limit.t
DBD-mysql-4.018/t/35prepare.t
DBD-mysql-4.018/t/40bindparam.t
DBD-mysql-4.018/t/40bindparam2.t
DBD-mysql-4.018/t/40blobs.t
DBD-mysql-4.018/t/40catalog.t
DBD-mysql-4.018/t/40keyinfo.t
DBD-mysql-4.018/t/40listfields.t
DBD-mysql-4.018/t/40nulls.t
DBD-mysql-4.018/t/40nulls_prepare.t
DBD-mysql-4.018/t/40numrows.t
DBD-mysql-4.018/t/40server_prepare.t
DBD-mysql-4.018/t/40server_prepare_error.t
DBD-mysql-4.018/t/40types.t
DBD-mysql-4.018/t/41bindparam.t
DBD-mysql-4.018/t/41blobs_prepare.t
DBD-mysql-4.018/t/42bindparam.t
DBD-mysql-4.018/t/50chopblanks.t
DBD-mysql-4.018/t/50commit.t
DBD-mysql-4.018/t/51bind_type_guessing.t
DBD-mysql-4.018/t/52comment.t
DBD-mysql-4.018/t/53comment.t
DBD-mysql-4.018/t/55utf8.t
DBD-mysql-4.018/t/60leaks.t
DBD-mysql-4.018/t/65types.t
DBD-mysql-4.018/t/70takeimp.t
DBD-mysql-4.018/t/71impdata.t
DBD-mysql-4.018/t/75supported_sql.t
DBD-mysql-4.018/t/76multi_statement.t
DBD-mysql-4.018/t/80procs.t
DBD-mysql-4.018/t/85init_command.t
DBD-mysql-4.018/t/86_bug_36972.t
DBD-mysql-4.018/t/lib.pl
DBD-mysql-4.018/t/mem_leak.pl
DBD-mysql-4.018/t/mysql.dbtest
DBD-mysql-4.018/t/mysql.mtest
DBD-mysql-4.018/TODO
CPAN: File::Temp loaded ok (v0.22)

  CPAN.pm: Going to build C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz

Can't exec "mysql_config": No such file or directory at Makefile.PL line 82.

Cannot find the file 'mysql_config'! Your execution PATH doesn't seem 
not contain the path to mysql_config. Resorting to guessed values!
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located


PLEASE NOTE:

For 'make test' to run properly, you must ensure that the 
database user 'root' can connect to your MySQL server 
and has the proper privileges that these tests require such 
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others. 

mysql> grant all privileges on test.* to 'root'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.PL --testuser=username

Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Failed to determine directory of mysql.h. Use

  perl Makefile.PL --cflags=-I<dir>

to set this directory. For details see the INSTALL.html file,
section "C Compiler flags" or type

  perl Makefile.PL --help
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  CAPTTOFU/DBD-mysql-4.018.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 CAPTTOFU/DBD-mysql-4.018.tar.gz              : writemakefile NO  '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512

[B]If I try and download the package manually, cd, and run perl for the makefile I get something similar:
[/B]

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# perl Makefile.PL --testuser=jill
Can't exec "mysql_config": No such file or directory at Makefile.PL line 76.

Cannot find the file 'mysql_config'! Your execution PATH doesn't seem 
not contain the path to mysql_config. Resorting to guessed values!
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Failed to determine directory of mysql.h. Use

  perl Makefile.PL --cflags=-I<dir>

to set this directory. For details see the INSTALL.html file,
section "C Compiler flags" or type

  perl Makefile.PL --help
[B]
If I try to download the package through the Ubuntu software center I'm  back to dependency issues. It won't let me download  mysql-cluster-client-5.1:[/B]

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# apt-get install libdbd-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdbd-mysql: Depends: libdbi0 (>= 0.8.2) but it is not going to be installed
  mysql-cluster-server-5.1: Depends: mysql-cluster-client-5.1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Help would be very, very appreciated.

Thanks!

---

### Post by mindlessbrain on 2010-11-21
I think I've got it now. I restarted my computer, and it told me I had some broken packages. After messing around a bit I removed that package and reinstalled it. Now when I type in the command "mysql" I go into a mysql base like cpan.

---

### Post by pande.mandy@gmail.com on 2011-02-10
[FONT=Trebuchet MS][SIZE=2][COLOR=Blue]Hi All,

Please help me out....am also facing the same problem. I tried several times, however getting same issue !

m get mad  :mad:[/COLOR][/SIZE][/FONT]
[COLOR=Blue]
Thanks,
Mandy.[/COLOR]

> **mindlessbrain said:**
> **Hello all,**

**I definitely don't have mysql installed. (Just to check)** 

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# mysql
The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1
Try: apt-get install <selected package>

[B]I can download the first two, but it won't let me download the last one through apt-get install.
  
If I try and install it through cpan I get:[/B]

cpan[6]> install DBD::mysql
Running install for module 'DBD::mysql'
Running make for C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz
  Has already been unwrapped into directory /root/.cpan/build/DBD-mysql-4.018-SIgigK
  '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512, won't make
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install

cpan[1]> force install DBD::mysql
CPAN: Storable loaded ok (v2.20)
Going to read '/root/.cpan/Metadata'
  Database was generated on Sun, 21 Nov 2010 07:42:41 GMT
Running install for module 'DBD::mysql'
CPAN: YAML loaded ok (v0.72)
Running make for C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz
CPAN: Digest::SHA loaded ok (v5.48)
CPAN: Compress::Zlib loaded ok (v2.03)
Checksum for /root/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz ok
Scanning cache /root/.cpan/build for sizes
............................................................................DONE
CPAN: Archive::Tar loaded ok (v1.72)
DBD-mysql-4.018/
DBD-mysql-4.018/ChangeLog
DBD-mysql-4.018/constants.h
DBD-mysql-4.018/dbdimp.c
DBD-mysql-4.018/dbdimp.h
DBD-mysql-4.018/eg/
DBD-mysql-4.018/eg/bug14979.pl
DBD-mysql-4.018/eg/bug21028.pl
DBD-mysql-4.018/eg/bug30033.pl
DBD-mysql-4.018/eg/bug30033pg.pl
DBD-mysql-4.018/eg/decimal_test.pl
DBD-mysql-4.018/eg/issue21946.pl
DBD-mysql-4.018/eg/prepare_memory_usage.pl
DBD-mysql-4.018/eg/proc_example1.pl
DBD-mysql-4.018/eg/proc_example2.pl
DBD-mysql-4.018/eg/proc_example2a.pl
DBD-mysql-4.018/eg/proc_example2b.pl
DBD-mysql-4.018/eg/proc_example3.pl
DBD-mysql-4.018/eg/proc_example4.pl
DBD-mysql-4.018/INSTALL.html
DBD-mysql-4.018/lib/
DBD-mysql-4.018/lib/Bundle/
DBD-mysql-4.018/lib/Bundle/DBD/
DBD-mysql-4.018/lib/Bundle/DBD/mysql.pm
DBD-mysql-4.018/lib/DBD/
DBD-mysql-4.018/lib/DBD/mysql/
DBD-mysql-4.018/lib/DBD/mysql/GetInfo.pm
DBD-mysql-4.018/lib/DBD/mysql/INSTALL.pod
DBD-mysql-4.018/lib/DBD/mysql.pm
DBD-mysql-4.018/Makefile.PL
DBD-mysql-4.018/Makefile.PL.embedded
DBD-mysql-4.018/MANIFEST
DBD-mysql-4.018/MANIFEST.SKIP
DBD-mysql-4.018/META.yml
DBD-mysql-4.018/myld
DBD-mysql-4.018/mysql.xs
DBD-mysql-4.018/README
DBD-mysql-4.018/t/
DBD-mysql-4.018/t/00base.t
DBD-mysql-4.018/t/10connect.t
DBD-mysql-4.018/t/20createdrop.t
DBD-mysql-4.018/t/25lockunlock.t
DBD-mysql-4.018/t/29warnings.t
DBD-mysql-4.018/t/30insertfetch.t
DBD-mysql-4.018/t/31insertid.t
DBD-mysql-4.018/t/32insert_error.t
DBD-mysql-4.018/t/35limit.t
DBD-mysql-4.018/t/35prepare.t
DBD-mysql-4.018/t/40bindparam.t
DBD-mysql-4.018/t/40bindparam2.t
DBD-mysql-4.018/t/40blobs.t
DBD-mysql-4.018/t/40catalog.t
DBD-mysql-4.018/t/40keyinfo.t
DBD-mysql-4.018/t/40listfields.t
DBD-mysql-4.018/t/40nulls.t
DBD-mysql-4.018/t/40nulls_prepare.t
DBD-mysql-4.018/t/40numrows.t
DBD-mysql-4.018/t/40server_prepare.t
DBD-mysql-4.018/t/40server_prepare_error.t
DBD-mysql-4.018/t/40types.t
DBD-mysql-4.018/t/41bindparam.t
DBD-mysql-4.018/t/41blobs_prepare.t
DBD-mysql-4.018/t/42bindparam.t
DBD-mysql-4.018/t/50chopblanks.t
DBD-mysql-4.018/t/50commit.t
DBD-mysql-4.018/t/51bind_type_guessing.t
DBD-mysql-4.018/t/52comment.t
DBD-mysql-4.018/t/53comment.t
DBD-mysql-4.018/t/55utf8.t
DBD-mysql-4.018/t/60leaks.t
DBD-mysql-4.018/t/65types.t
DBD-mysql-4.018/t/70takeimp.t
DBD-mysql-4.018/t/71impdata.t
DBD-mysql-4.018/t/75supported_sql.t
DBD-mysql-4.018/t/76multi_statement.t
DBD-mysql-4.018/t/80procs.t
DBD-mysql-4.018/t/85init_command.t
DBD-mysql-4.018/t/86_bug_36972.t
DBD-mysql-4.018/t/lib.pl
DBD-mysql-4.018/t/mem_leak.pl
DBD-mysql-4.018/t/mysql.dbtest
DBD-mysql-4.018/t/mysql.mtest
DBD-mysql-4.018/TODO
CPAN: File::Temp loaded ok (v0.22)

  CPAN.pm: Going to build C/CA/CAPTTOFU/DBD-mysql-4.018.tar.gz

Can't exec "mysql_config": No such file or directory at Makefile.PL line 82.

Cannot find the file 'mysql_config'! Your execution PATH doesn't seem 
not contain the path to mysql_config. Resorting to guessed values!
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located


PLEASE NOTE:

For 'make test' to run properly, you must ensure that the 
database user 'root' can connect to your MySQL server 
and has the proper privileges that these tests require such 
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others. 

mysql> grant all privileges on test.* to 'root'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.PL --testuser=username

Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 464.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Failed to determine directory of mysql.h. Use

  perl Makefile.PL --cflags=-I<dir>

to set this directory. For details see the INSTALL.html file,
section "C Compiler flags" or type

  perl Makefile.PL --help
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  CAPTTOFU/DBD-mysql-4.018.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 CAPTTOFU/DBD-mysql-4.018.tar.gz              : writemakefile NO  '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512

[B]If I try and download the package manually, cd, and run perl for the makefile I get something similar:
[/B]

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# perl Makefile.PL --testuser=jill
Can't exec "mysql_config": No such file or directory at Makefile.PL line 76.

Cannot find the file 'mysql_config'! Your execution PATH doesn't seem 
not contain the path to mysql_config. Resorting to guessed values!
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Failed to determine directory of mysql.h. Use

  perl Makefile.PL --cflags=-I<dir>

to set this directory. For details see the INSTALL.html file,
section "C Compiler flags" or type

  perl Makefile.PL --help
[B]
If I try to download the package through the Ubuntu software center I'm  back to dependency issues. It won't let me download  mysql-cluster-client-5.1:[/B]

root@jill-desktop:/home/jill/Desktop/DBD-mysql-4.011# apt-get install libdbd-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdbd-mysql: Depends: libdbi0 (>= 0.8.2) but it is not going to be installed
  mysql-cluster-server-5.1: Depends: mysql-cluster-client-5.1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Help would be very, very appreciated.

Thanks!

---

### Post by maomoa on 2011-04-11
You need to install the dev packages for mysql

sudo apt-get install libmysqlclient16-dev

Cheers!

---

### Post by golrokh on 2012-01-11
[B] Hi, 
Did you solve your problem??
And if so, could you plz tell me how, I have the same problem :(
Thanks
[/B]

---

