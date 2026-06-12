---
title: "kannel segmantation fault"
date: 2011-11-25
forum: General Help
---

### Post by vitotol on 2011-11-25
hello i want to generate a kannel licence on a fedora 15.

i run the command:

```
./bin/smppbox-lrrgen -u user -p pass -k etc/license.d/license_public.pem -o etc/license.d/smppbox.lrrV2 -V 2
```

the licence file is generated but the command returns me a
segmantation fault error.
on the /var/logs/messages i see this:

```
Nov 24 17:42:52 m1163 kernel: [781818.469076] smppbox-lrrgen[30049] general protection ip:3f29a9c8f8 sp:7fff14279f58 error:0 in libcrypto.so.1.0.0e[3f29a00000+174000]
```

the commands that shows the dependencies is
```
ldd sbin/smppbox-<version>
```

and it returns:
```
linux-vdso.so.1 =>  (0x00007fffe6b08000)
        libpam.so.0 => /lib64/libpam.so.0 (0x0000003e50200000)
        libdl.so.2 => /lib64/libdl.so.2 (0x000000354b000000)
        libpq.so.5 => /usr/lib64/libpq.so.5 (0x0000003f2a200000)
        libmysqlclient_r.so.16 => /usr/lib64/mysql/libmysqlclient_r.so.16 (0x00007f0ac1ebb000)
        libssl.so.8 => /usr/lib64/libssl.so.8 (0x0000003f29e00000)
        libpcreposix.so.0 => /usr/lib64/libpcreposix.so.0 (0x0000003568c00000)
        librt.so.1 => /lib64/librt.so.1 (0x0000003569800000)
        libresolv.so.2 => /lib64/libresolv.so.2 (0x000000356b000000)
        libnsl.so.1 => /lib64/libnsl.so.1 (0x000000356bc00000)
        libm.so.6 => /lib64/libm.so.6 (0x000000356a400000)
        libpthread.so.0 => /lib64/libpthread.so.0 (0x0000003569000000)
        libxml2.so.2 => /usr/lib64/libxml2.so.2 (0x000000354c800000)
        libz.so.1 => /lib64/libz.so.1 (0x000000354b800000)
        libpcre.so.0 => /lib64/libpcre.so.0 (0x0000003569400000)
        libcrypto.so.8 => /usr/lib64/libcrypto.so.8 (0x0000003f29a00000)
        libcrypt.so.1 => /lib64/libcrypt.so.1 (0x000000354d400000)
        libsqlite3.so.0 => /usr/lib64/libsqlite3.so.0 (0x00007f0ac1c1d000)
        libc.so.6 => /lib64/libc.so.6 (0x0000003568800000)
        libaudit.so.1 => /lib64/libaudit.so.1 (0x00007f0ac1a04000)
        /lib64/ld-linux-x86-64.so.2 (0x0000003568400000)
        libkrb5.so.3 => /lib64/libkrb5.so.3 (0x0000003f58e00000)
        libcom_err.so.2 => /lib64/libcom_err.so.2 (0x000000356b400000)
        libgssapi_krb5.so.2 => /lib64/libgssapi_krb5.so.2 (0x0000003f59a00000)
        libldap_r-2.4.so.2 => /usr/lib64/libldap_r-2.4.so.2 (0x0000003025e00000)
        libk5crypto.so.3 => /lib64/libk5crypto.so.3 (0x0000003f59200000)
        libfreebl3.so => /lib64/libfreebl3.so (0x000000354a400000)
        libkrb5support.so.0 => /lib64/libkrb5support.so.0 (0x0000003f59600000)
        libkeyutils.so.1 => /lib64/libkeyutils.so.1 (0x000000354b400000)
        liblber-2.4.so.2 => /usr/lib64/liblber-2.4.so.2 (0x0000003e50e00000)
        libssl3.so => /usr/lib64/libssl3.so (0x0000003e4fe00000)
        libsmime3.so => /usr/lib64/libsmime3.so (0x0000003e4fa00000)
        libnss3.so => /usr/lib64/libnss3.so (0x0000003e4ea00000)
        libnssutil3.so => /usr/lib64/libnssutil3.so (0x0000003e4f200000)
        libplds4.so => /lib64/libplds4.so (0x0000003e4ee00000)
        libplc4.so => /lib64/libplc4.so (0x0000003e4f600000)
        libnspr4.so => /lib64/libnspr4.so (0x0000003e4e600000)
        libsasl2.so.2 => /usr/lib64/libsasl2.so.2 (0x0000003e50600000)
        libselinux.so.1 => /lib64/libselinux.so.1 (0x000000354bc00000)
```

some dependencies problems solved by creating symbolic links.
for example i have the libcrypto.so.10 on the system but i needed the 8 so i created a symbolic link libcrypto.so.8 ---> libcrypto.so.10.

can someone help me?

---

### Post by vitotol on 2011-12-02
hello again... the libc wasn't compatible. i downloaded a newer version of the package and it worked fine.

---

