---
title: "SVN not working after upgrade to Karmic"
date: 2010-02-20
forum: General Help
---

### Post by newbie_newbie on 2010-02-20
Hey folks,

I upgraded my machine to Ubuntu 9.10 and my subversion is not able to find the shared lib: libmysqlclient_r.so.15.

"svn: error while loading shared libraries: libmysqlclient_r.so.15: cannot open shared object file: No such file or directory"

I removed the subversion and install it again which did not solve my problem.

$ ldd `which svn` 
	linux-gate.so.1 =>  (0x00242000)
	libsvn_client-1.so.0 => /usr/local/lib/libsvn_client-1.so.0 (0x004ac000)
	libsvn_wc-1.so.0 => /usr/local/lib/libsvn_wc-1.so.0 (0x00563000)
	libsvn_ra-1.so.0 => /usr/local/lib/libsvn_ra-1.so.0 (0x00f83000)
	libsvn_diff-1.so.0 => /usr/local/lib/libsvn_diff-1.so.0 (0x00aa1000)
	libsvn_ra_local-1.so.0 => /usr/local/lib/libsvn_ra_local-1.so.0 (0x0069b000)
	libsvn_repos-1.so.0 => /usr/local/lib/libsvn_repos-1.so.0 (0x0034d000)
	libsvn_fs-1.so.0 => /usr/local/lib/libsvn_fs-1.so.0 (0x00955000)
	libsvn_fs_fs-1.so.0 => /usr/local/lib/libsvn_fs_fs-1.so.0 (0x00bd4000)
	libsvn_fs_util-1.so.0 => /usr/local/lib/libsvn_fs_util-1.so.0 (0x00219000)
	libsvn_ra_svn-1.so.0 => /usr/local/lib/libsvn_ra_svn-1.so.0 (0x00c48000)
	libsvn_ra_neon-1.so.0 => /usr/local/lib/libsvn_ra_neon-1.so.0 (0x0080d000)
	libsvn_delta-1.so.0 => /usr/local/lib/libsvn_delta-1.so.0 (0x00d60000)
	libsvn_subr-1.so.0 => /usr/local/lib/libsvn_subr-1.so.0 (0x002d1000)
	libaprutil-1.so.0 => /usr/lib/libaprutil-1.so.0 (0x006e4000)
	libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x00b84000)
	liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x00110000)
	libdb-4.6.so => /usr/lib/libdb-4.6.so (0x0095d000)
	libpq.so.5 => /usr/lib/libpq.so.5 (0x00f27000)
**	libmysqlclient_r.so.15 => not found**
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x0011f000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00136000)
	libz.so.1 => /lib/libz.so.1 (0x00eda000)
	libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x0015c000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00ea7000)
	libapr-1.so.0 => /usr/lib/libapr-1.so.0 (0x00e38000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00af4000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x001fb000)
	libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0x00243000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00f99000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x001e4000)
	libneon.so.27 => /usr/lib/libneon.so.27 (0x00c77000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00fb2000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x00204000)
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x003ff000)
	libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x005a7000)
	libssl.so.0.9.8 => /lib/i686/cmov/libssl.so.0.9.8 (0x00275000)
	libcrypto.so.0.9.8 => /lib/i686/cmov/libcrypto.so.0.9.8 (0x042ee000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x00707000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0x001e8000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00319000)
	/lib/ld-linux.so.2 (0x006a8000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00374000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x01901000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x00f0d000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x00419000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x001ec000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x001f4000)


I want to know how to get the missing libmysqlclient_r.so.15 library. I havelibmysqlclient_r.so.16 though.

[B]$sudo find / -name libmysqlclient_r.so.*
/usr/lib/libmysqlclient_r.so.16
/usr/lib/libmysqlclient_r.so.16.0.0[/B]



Thanks,
SJ

---

### Post by gmargo on 2010-02-20
> **newbie_newbie said:**
> 
$ ldd `which svn` 
    linux-gate.so.1 =>  (0x00242000)
    libsvn_client-1.so.0 => **/usr/local/lib/**libsvn_client-1.so.0 (0x004ac000)
    libsvn_wc-1.so.0 => **/usr/local/lib/**libsvn_wc-1.so.0 (0x00563000)
    libsvn_ra-1.so.0 => **/usr/local/lib/**libsvn_ra-1.so.0 (0x00f83000)
    libsvn_diff-1.so.0 => **/usr/local/lib/**libsvn_diff-1.so.0 (0x00aa1000)
...
**    libmysqlclient_r.so.15 => not found**
   


I think your $PATH is hitting **/usr/local/bin/svn**, a version you compiled yourself.  Remove that one and use the Ubuntu one in **/usr/bin/svn**.

---

