---
title: "Determine config options used when DEB was compiled"
date: 2012-09-26
forum: General Help
---

### Post by david.rahrer on 2012-09-26
I want to compile a current version of php5-fpm from source for use on a server running Ubuntu 12.04.  I can do this using the default options, but would like to know if there is a way to determine what options were actually used when the existing version (5.3.10-1ubuntu3.4) was built into a deb.  As I understand it, 95% of the apps in the official repositories use the defaults, but I would like to be sure.  

I know when using ffmpeg from the command line, it spits out the options used to compile it.  I thought there may be a way to do this for others, but so far I haven't found anything.

Thanks.

---

### Post by Rexilion on 2012-09-27
If you search at packages.ubuntu.com and click on the package you can find the original (hopefull unmodificied ;) source tarball) along with the Ubuntu specific 'goop' that forms the source deb. Inside the ubuntu goop tarball you will find everything that is required to build the beast.

Not *entirely* sure, but:

> +configure-fpm-stamp: prepared-stamp
+	dh_testdir
+	if [ -d fpm-build ]; then rm -rf fpm-build; fi
+	-mkdir fpm-build
+	cd fpm-build && \
+        CFLAGS="$(CFLAGS)" PROG_SENDMAIL="$(PROG_SENDMAIL)" ../configure \
+		--prefix=/usr --enable-fpm --disable-cgi \
+		--with-fpm-user=www-data --with-fpm-group=www-data \
+		--with-config-file-path=/etc/php5/fpm \
+		--with-config-file-scan-dir=/etc/php5/fpm/conf.d \
+		$(COMMON_CONFIG) \
+		--with-libevent-dir=/usr \
+		--without-mm \
+		--disable-pdo \
+		--without-mysql --without-sybase-ct --without-sqlite \
+		--without-mssql --without-sqlite3
+	cd fpm-build && \
+	cp ../Zend/zend_ini_scanner.c ../Zend/zend_language_scanner.c \
+	   ../Zend/zend_ini_parser.h ../Zend/zend_language_parser.h \
+	   ../Zend/zend_ini_parser.c ../Zend/zend_language_parser.c \
+	   Zend/
+	touch configure-fpm-stamp
+


---

### Post by david.rahrer on 2012-09-27
Very cool idea, I'll give it a try and report back.  Thanks!

---

