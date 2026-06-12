---
title: "Python Error message always comes up"
date: 2012-01-08
forum: General Help
---

### Post by joneeeeees on 2012-01-08
Hello, 
everytime I type something into the console that gives an error (eg. command not found) I also get these two errors:
```

/usr/bin/python: /usr/local/lib/libcrypto.so.1.0.0: no version information available (required by /usr/bin/python)
/usr/bin/python: /usr/local/lib/libssl.so.1.0.0: no version information available (required by /usr/bin/python)

```Apparently this has something to do with systemvariables and the installation of two versions of these libraries: 
```

$ locate libcrypto.so.1.0.0
/lib/i386-linux-gnu/libcrypto.so.1.0.0
/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/lib32/libcrypto.so.1.0.0
/usr/lib/i386-linux-gnu/libcrypto.so.1.0.0
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/usr/lib32/libcrypto.so.1.0.0
/usr/local/lib/libcrypto.so.1.0.0
/usr/local/src/Amap/openssl-1.0.0e/libcrypto.so.1.0.0

```and 

```

$ locate libcrypto.so.1.0.0
/lib/i386-linux-gnu/libcrypto.so.1.0.0
/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/lib32/libcrypto.so.1.0.0
/usr/lib/i386-linux-gnu/libcrypto.so.1.0.0
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/usr/lib32/libcrypto.so.1.0.0
/usr/local/lib/libcrypto.so.1.0.0
/usr/local/src/Amap/openssl-1.0.0e/libcrypto.so.1.0.0

```
But I have no clue how to fix it. Can someone help? Thanks,
Jones

---

### Post by mattcasw on 2012-06-09
I've had this same problem for a little while. It is just a warning message and can be safely ignored.

However, for me, it was driving me nuts. After a bit of digging around I have managed to resolve this although it took a little effort.

You said that you have two versions of the openssl libraries installed. I assume that your second copy came from a source install. If not you may be out of luck, because my solution won't work for you.

The problem is that ubuntu binaries linked to libcrypto and libssl (e.g. /usr/bin/ssh) expect symbol version information to be available in the shared libraries.

For example if I run the following without the built-from-source libraries in the library path:

ldd -v /usr/bin/ssh | grep crypto

I get this output:
...
        libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007f856b09c000)
...
        Version information:
        /usr/bin/ssh:
                libdl.so.2 (GLIBC_2.2.5) => /lib/x86_64-linux-gnu/libdl.so.2
                libresolv.so.2 (GLIBC_2.2.5) => /lib/x86_64-linux-gnu/libresolv.so.2
                libgssapi_krb5.so.2 (gssapi_krb5_2_MIT) => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2
                libcrypto.so.1.0.0 (OPENSSL_1.0.0) => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
...

But running with built-from-source libraries in the path I get:
...
        libcrypto.so.1.0.0 => /usr/local/ssl/lib/libcrypto.so.1.0.0 (0x00007fceb4d4b000)
...
        Version information:
        /usr/bin/ssh:
                libdl.so.2 (GLIBC_2.2.5) => /lib/x86_64-linux-gnu/libdl.so.2
                libresolv.so.2 (GLIBC_2.2.5) => /lib/x86_64-linux-gnu/libresolv.so.2
                libgssapi_krb5.so.2 (gssapi_krb5_2_MIT) => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2
                libcrypto.so.1.0.0 (OPENSSL_1.0.0) => not found
...


My solution is to build from source but ensure the version information is included. Unfortunately this information does not get into the build through the source distributed by the OpenSSL project. It is actually added as a patch provided by the ubuntu/debian package maintainers. First step is to download the source for the ubuntu package. I got it from here (for 12.04):
[http://packages.ubuntu.com/source/precise/openssl](http://packages.ubuntu.com/source/precise/openssl)

Download the debian.tar.gz file, unzip and extract it. You are after the file debian/patches/version-script.patch

Now go back to the directory where your openssl source is (i.e. the source you downloaded from openssl.org...or wherever) and type the following:

patch -p1 </PATH_TO_THE_FILE_HERE/version-script.patch

You need to re-run the config script, and then make as normal, e.g. typically:
./config shared
make
make test
make install

Hopefully it should all now work without the warning message!

Matt

---

