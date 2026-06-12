---
title: "openssh 5.9p1 patch and LDAP"
date: 2012-06-27
forum: General Help
---

### Post by xtech on 2012-06-27
hello, i'm trying to patch openssh5.9p1 with openssh-lpk patch on ubuntu 12.04LTS, but have some troubles with package building.
Without "confflags += --with-ldap" flag in debian/rules, package builds fine, but with the flag I have following error:


```
checking for LDAP support... no
configure: error: ** Incomplete or missing ldap libraries **
dh_auto_configure: ../configure --build=x86_64-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/openssh --disable-maintainer-mode --disable-dependency-tracking --sysconfdir=/etc/ssh --disable-strip --with-mantype=doc --with-4in6 --with-privsep-path=/var/run/sshd --with-tcp-wrappers --with-pam --with-libedit --with-kerberos5=/usr --with-ssl-engine --with-selinux --with-consolekit --with-xauth=/usr/bin/xauth --with-ldap --with-default-path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games --with-superuser-path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11 --with-cflags=-D_FORTIFY_SOURCE=2 -g -O2 -fPIE -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -DLOGIN_PROGRAM=\"/bin/login\" -DLOGIN_NO_ENDOPT -DSSH_EXTRAVERSION=\"Debian-5ubuntu1\" --with-ldflags=-Wl,--as-needed -Wl,-Bsymbolic-functions -fPIE -pie -Wl,-z,relro -Wl,-z,now returned exit code 1
make[1]: *** [override_dh_auto_configure] Error 2
make[1]: Leaving directory `/usr/src/openssh-5.9p1'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

---

