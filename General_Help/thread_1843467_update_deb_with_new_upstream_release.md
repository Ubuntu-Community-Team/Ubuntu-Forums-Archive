---
title: "update deb with new upstream release"
date: 2011-09-13
forum: General Help
---

### Post by mindo on 2011-09-13
Hi,

I am trying to update freetds packages. The version on the repos is 0.82 but i need the lastest one (bug fixes and features).
These are the steps i made:

```

apt-get source freetds
wget [ftp://ftp.ibiblio.org/pub/Linux/ALPHA/freetds/stable/freetds-0.91.tar.gz](ftp://ftp.ibiblio.org/pub/Linux/ALPHA/freetds/stable/freetds-0.91.tar.gz)
cd freetds-0.82
uupdate ../freetds-0.91.tar.gz
cd freetds-0.91
dpkg-buildpackage -rfakeroot 

```

At this point the build fails. First because the patch from v0.82 adds some lines to mem.c and locale.c that don't work anymore and after deleting them with this error:

```

+#MISSING: 0.91-0ubuntu1# open_commit@Base 0.63
+#MISSING: 0.91-0ubuntu1# remove_xact@Base 0.63
+#MISSING: 0.91-0ubuntu1# scan_xact@Base 0.63
+#MISSING: 0.91-0ubuntu1# start_xact@Base 0.63
+#MISSING: 0.91-0ubuntu1# stat_xact@Base 0.63
  tdsdbopen@Base 0.63
  tdsdump_open@Base 0.63
dh_makeshlibs: dpkg-gensymbols -plibsybdb5 -Idebian/libsybdb5.symbols -Pdebian/libsybdb5 returned exit code 1
make[1]: *** [override_dh_makeshlibs] Error 1
make[1]: Leaving directory `/mnt/old/ams/Work/Work/building/packaging/tmp/freetds-0.91'
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2

```

The weird thing is that freetds is built - if i look into debian/tmp i can see all the files there, so the problem appears to be only when assembling the deb files.

Am I missing any step? If not, anyone has any idea why this is happenning?

---

### Post by Saosin7 on 2011-09-19
I have the same problem. [Posted a question about it]("http://serverfault.com/questions/312895/compiling-freetds-0-91-on-ubuntu-11-04-x64") over at Server Fault.

---

