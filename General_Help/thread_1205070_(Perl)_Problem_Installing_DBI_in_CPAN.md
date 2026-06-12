---
title: "(Perl) Problem Installing DBI in CPAN"
date: 2009-07-05
forum: General Help
---

### Post by stephenmcgowan on 2009-07-05
Hi,

I'm trying to install DBI from CPAN.

I logged into CPAN with: sudo perl -MCPAN -e shell

cpan> install DBI

I haven't much of a clue why the install is falling over... below is the feedback i get:


Install feedback
-----------------------------------

cpan> install DBI
CPAN: Storable loaded ok
Going to read /Users/stevey_mac2k2/.cpan/Metadata
  Database was generated on Sat, 04 Jul 2009 23:26:56 GMT
Running install for module DBI
Running make for T/TI/TIMB/DBI-1.609.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /Users/stevey_mac2k2/.cpan/sources/authors/id/T/TI/TIMB/DBI-1.609.tar.gz ok
Scanning cache /Users/stevey_mac2k2/.cpan/build for sizes
DBI-1.609/
DBI-1.609/Changes
DBI-1.609/dbd_xsh.h
DBI-1.609/DBI.pm
DBI-1.609/DBI.xs
DBI-1.609/dbi_sql.h
DBI-1.609/dbilogstrip.PL
DBI-1.609/dbipport.h
DBI-1.609/dbiprof.PL
DBI-1.609/dbiproxy.PL
DBI-1.609/dbivport.h
DBI-1.609/DBIXS.h
DBI-1.609/dbixs_rev.h
DBI-1.609/dbixs_rev.pl
DBI-1.609/Driver.xst
DBI-1.609/Driver_xst.h
DBI-1.609/ex/
DBI-1.609/ex/perl_dbi_nulls_test.pl
DBI-1.609/ex/profile.pl
DBI-1.609/lib/
DBI-1.609/lib/Bundle/
DBI-1.609/lib/Bundle/DBI.pm
DBI-1.609/lib/DBD/
DBI-1.609/lib/DBD/DBM.pm
DBI-1.609/lib/DBD/ExampleP.pm
DBI-1.609/lib/DBD/File.pm
DBI-1.609/lib/DBD/Gofer/
DBI-1.609/lib/DBD/Gofer/Policy/
DBI-1.609/lib/DBD/Gofer/Policy/Base.pm
DBI-1.609/lib/DBD/Gofer/Policy/classic.pm
DBI-1.609/lib/DBD/Gofer/Policy/pedantic.pm
DBI-1.609/lib/DBD/Gofer/Policy/rush.pm
DBI-1.609/lib/DBD/Gofer/Transport/
DBI-1.609/lib/DBD/Gofer/Transport/Base.pm
DBI-1.609/lib/DBD/Gofer/Transport/null.pm
DBI-1.609/lib/DBD/Gofer/Transport/pipeone.pm
DBI-1.609/lib/DBD/Gofer/Transport/stream.pm
DBI-1.609/lib/DBD/Gofer.pm
DBI-1.609/lib/DBD/NullP.pm
DBI-1.609/lib/DBD/Proxy.pm
DBI-1.609/lib/DBD/Sponge.pm
DBI-1.609/lib/DBI/
DBI-1.609/lib/DBI/Const/
DBI-1.609/lib/DBI/Const/GetInfo/
DBI-1.609/lib/DBI/Const/GetInfo/ANSI.pm
DBI-1.609/lib/DBI/Const/GetInfo/ODBC.pm
DBI-1.609/lib/DBI/Const/GetInfoReturn.pm
DBI-1.609/lib/DBI/Const/GetInfoType.pm
DBI-1.609/lib/DBI/DBD/
DBI-1.609/lib/DBI/DBD/Metadata.pm
DBI-1.609/lib/DBI/DBD.pm
DBI-1.609/lib/DBI/FAQ.pm
DBI-1.609/lib/DBI/Gofer/
DBI-1.609/lib/DBI/Gofer/Execute.pm
DBI-1.609/lib/DBI/Gofer/Request.pm
DBI-1.609/lib/DBI/Gofer/Response.pm
DBI-1.609/lib/DBI/Gofer/Serializer/
DBI-1.609/lib/DBI/Gofer/Serializer/Base.pm
DBI-1.609/lib/DBI/Gofer/Serializer/DataDumper.pm
DBI-1.609/lib/DBI/Gofer/Serializer/Storable.pm
DBI-1.609/lib/DBI/Gofer/Transport/
DBI-1.609/lib/DBI/Gofer/Transport/Base.pm
DBI-1.609/lib/DBI/Gofer/Transport/pipeone.pm
DBI-1.609/lib/DBI/Gofer/Transport/stream.pm
DBI-1.609/lib/DBI/Profile.pm
DBI-1.609/lib/DBI/ProfileData.pm
DBI-1.609/lib/DBI/ProfileDumper/
DBI-1.609/lib/DBI/ProfileDumper/Apache.pm
DBI-1.609/lib/DBI/ProfileDumper.pm
DBI-1.609/lib/DBI/ProfileSubs.pm
DBI-1.609/lib/DBI/ProxyServer.pm
DBI-1.609/lib/DBI/PurePerl.pm
DBI-1.609/lib/DBI/SQL/
DBI-1.609/lib/DBI/SQL/Nano.pm
DBI-1.609/lib/DBI/Util/
DBI-1.609/lib/DBI/Util/_accessor.pm
DBI-1.609/lib/DBI/Util/CacheMemory.pm
DBI-1.609/lib/DBI/W32ODBC.pm
DBI-1.609/lib/Win32/
DBI-1.609/lib/Win32/DBIODBC.pm
DBI-1.609/Makefile.PL
DBI-1.609/MANIFEST
DBI-1.609/META.yml
DBI-1.609/Perl.xs
DBI-1.609/README
DBI-1.609/Roadmap.pod
DBI-1.609/t/
DBI-1.609/t/01basics.t
DBI-1.609/t/02dbidrv.t
DBI-1.609/t/03handle.t
DBI-1.609/t/04mods.t
DBI-1.609/t/05concathash.t
DBI-1.609/t/06attrs.t
DBI-1.609/t/07kids.t
DBI-1.609/t/08keeperr.t
DBI-1.609/t/09trace.t
DBI-1.609/t/10examp.t
DBI-1.609/t/11fetch.t
DBI-1.609/t/12quote.t
DBI-1.609/t/13taint.t
DBI-1.609/t/14utf8.t
DBI-1.609/t/15array.t
DBI-1.609/t/19fhtrace.t
DBI-1.609/t/20meta.t
DBI-1.609/t/30subclass.t
DBI-1.609/t/35thrclone.t
DBI-1.609/t/40profile.t
DBI-1.609/t/41prof_dump.t
DBI-1.609/t/42prof_data.t
DBI-1.609/t/43prof_env.t
DBI-1.609/t/50dbm.t
DBI-1.609/t/60preparse.t
DBI-1.609/t/65transact.t
DBI-1.609/t/70callbacks.t
DBI-1.609/t/72childhandles.t
DBI-1.609/t/80proxy.t
DBI-1.609/t/85gofer.t
DBI-1.609/t/86gofer_fail.t
DBI-1.609/t/87gofer_cache.t
DBI-1.609/t/pod-coverage.t
DBI-1.609/t/pod.t
DBI-1.609/TASKS.pod
DBI-1.609/test.pl
DBI-1.609/TODO_2005.txt
DBI-1.609/TODO_gofer.txt
DBI-1.609/typemap
Removing previously used /Users/stevey_mac2k2/.cpan/build/DBI-1.609

  CPAN.pm: Going to build T/TI/TIMB/DBI-1.609.tar.gz


*** Your LANG environment variable is set to 'en_GB.UTF-8'
*** This may cause problems for some perl installations.
*** If you get test failures, please try again with LANG unset.
*** If that then works, please email [email]dbi-dev@perl.org[/email] with details
*** including the output of 'perl -V'


*** You are using a perl configured with threading enabled.
*** You should be aware that using multiple threads is
*** not recommended for production environments.

Your perl was compiled with gcc (version 4.0.1 (Apple Inc. build 5465)), okay.
Creating test wrappers for DBI::PurePerl:
t/zvp_01basics.t 
t/zvp_02dbidrv.t 
t/zvp_03handle.t 
t/zvp_04mods.t 
t/zvp_05concathash.t 
t/zvp_06attrs.t 
t/zvp_07kids.t 
t/zvp_08keeperr.t 
t/zvp_09trace.t 
t/zvp_10examp.t 
t/zvp_11fetch.t 
t/zvp_12quote.t 
t/zvp_13taint.t 
t/zvp_14utf8.t 
t/zvp_15array.t 
t/zvp_19fhtrace.t 
t/zvp_20meta.t 
t/zvp_30subclass.t 
t/zvp_35thrclone.t (use threads)
t/zvp_40profile.t 
t/zvp_41prof_dump.t 
t/zvp_42prof_data.t 
t/zvp_43prof_env.t 
t/zvp_50dbm.t 
t/zvp_60preparse.t 
t/zvp_65transact.t 
t/zvp_70callbacks.t 
t/zvp_72childhandles.t 
t/zvp_80proxy.t 
t/zvp_85gofer.t 
t/zvp_86gofer_fail.t 
t/zvp_87gofer_cache.t 
Creating test wrappers for DBD::Gofer:
t/zvg_01basics.t 
t/zvg_02dbidrv.t 
t/zvg_03handle.t 
t/zvg_04mods.t 
t/zvg_05concathash.t 
t/zvg_06attrs.t 
t/zvg_07kids.t 
t/zvg_08keeperr.t 
t/zvg_09trace.t 
t/zvg_10examp.t 
t/zvg_11fetch.t 
t/zvg_12quote.t 
t/zvg_13taint.t 
t/zvg_14utf8.t 
t/zvg_15array.t 
t/zvg_19fhtrace.t 
t/zvg_20meta.t 
t/zvg_30subclass.t 
t/zvg_35thrclone.t (use threads)
t/zvg_40profile.t 
t/zvg_41prof_dump.t 
t/zvg_42prof_data.t 
t/zvg_43prof_env.t 
t/zvg_50dbm.t 
t/zvg_60preparse.t 
t/zvg_65transact.t 
t/zvg_70callbacks.t 
t/zvg_72childhandles.t 
t/zvg_80proxy.t 
t/zvg_85gofer.t 
t/zvg_86gofer_fail.t 
t/zvg_87gofer_cache.t 
Creating test wrappers for PurePerl & Gofer:
t/zvxgp_01basics.t 
t/zvxgp_02dbidrv.t 
t/zvxgp_03handle.t 
t/zvxgp_04mods.t 
t/zvxgp_05concathash.t 
t/zvxgp_06attrs.t 
t/zvxgp_07kids.t 
t/zvxgp_08keeperr.t 
t/zvxgp_09trace.t 
t/zvxgp_10examp.t 
t/zvxgp_11fetch.t 
t/zvxgp_12quote.t 
t/zvxgp_13taint.t 
t/zvxgp_14utf8.t 
t/zvxgp_15array.t 
t/zvxgp_19fhtrace.t 
t/zvxgp_20meta.t 
t/zvxgp_30subclass.t 
t/zvxgp_35thrclone.t (use threads)
t/zvxgp_40profile.t 
t/zvxgp_41prof_dump.t 
t/zvxgp_42prof_data.t 
t/zvxgp_43prof_env.t 
t/zvxgp_50dbm.t 
t/zvxgp_60preparse.t 
t/zvxgp_65transact.t 
t/zvxgp_70callbacks.t 
t/zvxgp_72childhandles.t 
t/zvxgp_80proxy.t 
t/zvxgp_85gofer.t 
t/zvxgp_86gofer_fail.t 
t/zvxgp_87gofer_cache.t 
Checking if your kit is complete...
Looks good

    I see you're using perl 5.008008 on darwin-thread-multi-2level, okay.
    Remember to actually *read* the README file!
    Use  'make' to build the software (dmake or nmake on Windows).
    Then 'make test' to execute self tests.
    Then 'make install' to install the DBI and then delete this working
    directory before unpacking and building any DBD::* drivers.

Writing Makefile for DBI
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

Thanks,

Stephen

---

### Post by sanderj on 2009-07-05
Try:

```

sudo perl -MCPAN -e 'install DBI'

```

That works for me on Ubuntu 9.04

---

