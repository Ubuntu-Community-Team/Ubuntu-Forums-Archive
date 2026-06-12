---
title: "QT Everywhere Opensource 4.7.4 on Ubuntu 10.04"
date: 2011-11-03
forum: General Help
---

### Post by HoeHum on 2011-11-03
Hi all,

After losing faith in Fedora I moved over to Ubuntu but have hit another stumbling block whilst trying to get QT4.7.4 running -

I'm trying to build with phonon included as so

> 
./configure -v -embedded arm -xplatform qws/linux-arm-imx -phonon -force-pkg-config
This gives;

```

Creating qmake. Please wait...
make: Nothing to be done for `first'.
floatmath auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o floatmath.o floatmath.cpp
floatmath.cpp:44: warning: unused parameter 'argc'
floatmath.cpp:44: warning: unused parameter 'argv'
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -Wl,-O1 -o floatmath floatmath.o      
floatmath enabled.
mmx auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -mmmx -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o mmx.o mmx.cpp
cc1plus: error: unrecognized command line option "-mmmx"
make: *** [mmx.o] Error 1
mmx disabled.
3dnow auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -m3dnow -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o 3dnow.o 3dnow.cpp
cc1plus: error: unrecognized command line option "-m3dnow"
make: *** [3dnow.o] Error 1
3dnow disabled.
sse auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -msse -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sse.o sse.cpp
cc1plus: error: unrecognized command line option "-msse"
make: *** [sse.o] Error 1
sse disabled.
sse2 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -msse2 -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sse2.o sse2.cpp
cc1plus: error: unrecognized command line option "-msse2"
make: *** [sse2.o] Error 1
sse2 disabled.
sse3 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -msse3 -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sse3.o sse3.cpp
cc1plus: error: unrecognized command line option "-msse3"
make: *** [sse3.o] Error 1
sse3 disabled.
ssse3 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -mssse3 -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o ssse3.o ssse3.cpp
cc1plus: error: unrecognized command line option "-mssse3"
make: *** [ssse3.o] Error 1
ssse3 disabled.
sse4_1 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -msse4.1 -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sse4_1.o sse4_1.cpp
cc1plus: error: unrecognized command line option "-msse4.1"
make: *** [sse4_1.o] Error 1
sse4_1 disabled.
sse4_2 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -msse4.2 -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sse4_2.o sse4_2.cpp
cc1plus: error: unrecognized command line option "-msse4.2"
make: *** [sse4_2.o] Error 1
sse4_2 disabled.
avx auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -mavx -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o avx.o avx.cpp
cc1plus: error: unrecognized command line option "-mavx"
make: *** [avx.o] Error 1
avx disabled.
neon auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -mfpu=neon -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o neon.o neon.cpp
Assembler messages:
Error: unknown floating point format `neon'

Error: unrecognized option -mfpu=neon
neon.cpp:1: error: invalid floating point option: -mfpu=neon
make: *** [neon.o] Error 1
neon disabled.
zlib auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o zlib.o zlib.cpp
zlib.cpp:42:18: error: zlib.h: No such file or directory
zlib.cpp: In function 'int main(int, char**)':
zlib.cpp:46: error: 'z_streamp' was not declared in this scope
zlib.cpp:46: error: expected `;' before 'stream'
zlib.cpp:47: error: 'stream' was not declared in this scope
zlib.cpp:48: error: 'zlibVersion' was not declared in this scope
zlib.cpp:51: error: 'compress2' was not declared in this scope
make: *** [zlib.o] Error 1
zlib disabled.
libjpeg auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o libjpeg.o libjpeg.cpp
libjpeg.cpp:45:21: error: jpeglib.h: No such file or directory
libjpeg.cpp: In function 'int main(int, char**)':
libjpeg.cpp:50: error: 'j_compress_ptr' was not declared in this scope
libjpeg.cpp:50: error: expected `;' before 'cinfo'
libjpeg.cpp:51: error: 'cinfo' was not declared in this scope
libjpeg.cpp:51: error: 'jpeg_create_compress' was not declared in this scope
make: *** [libjpeg.o] Error 1
libjpeg disabled.
libtiff auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o libtiff.o libtiff.cpp
libtiff.cpp:42:20: error: tiffio.h: No such file or directory
libtiff.cpp:50:6: error: #error "Required libtiff not found"
libtiff.cpp: In function 'int main(int, char**)':
libtiff.cpp:57: error: 'tdata_t' was not declared in this scope
libtiff.cpp:57: error: expected `;' before 'buffer'
libtiff.cpp:58: error: 'buffer' was not declared in this scope
libtiff.cpp:58: error: '_TIFFfree' was not declared in this scope
libtiff.cpp:62: error: 'TIFFReadRGBAImageOriented' was not declared in this scope
make: *** [libtiff.o] Error 1
libtiff disabled.
libmng auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o libmng.o libmng.cpp
libmng.cpp:42:20: error: libmng.h: No such file or directory
libmng.cpp:50:2: error: #error System libmng version is less than 1.0.9; using built-in version instead.
libmng.cpp: In function 'int main(int, char**)':
libmng.cpp:46: error: 'mng_handle' was not declared in this scope
libmng.cpp:46: error: expected `;' before 'hMNG'
libmng.cpp:47: error: 'hMNG' was not declared in this scope
libmng.cpp:47: error: 'mng_cleanup' was not declared in this scope
make: *** [libmng.o] Error 1
libmng disabled.
libpng auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o libpng.o libpng.cpp
libpng.cpp:42:17: error: png.h: No such file or directory
libpng.cpp:45:4: error: #error "Required libpng version 1.0.17 not found."
libpng.cpp: In function 'int main(int, char**)':
libpng.cpp:50: error: 'png_structp' was not declared in this scope
libpng.cpp:50: error: expected `;' before 'png_ptr'
libpng.cpp:51: error: 'png_ptr' was not declared in this scope
libpng.cpp:51: error: 'PNG_LIBPNG_VER_STRING' was not declared in this scope
libpng.cpp:51: error: 'png_create_read_struct' was not declared in this scope
make: *** [libpng.o] Error 1
libpng disabled.
DB2 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o db2.o db2.cpp
db2.cpp:42:20: error: sqlcli.h: No such file or directory
db2.cpp:43:21: error: sqlcli1.h: No such file or directory
make: *** [db2.o] Error 1
DB2 disabled.
InterBase auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o ibase.o ibase.cpp
ibase.cpp:42:19: error: ibase.h: No such file or directory
make: *** [ibase.o] Error 1
InterBase disabled.
MySQL (thread-safe) auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o mysql.o ../mysql/mysql.cpp
../mysql/mysql.cpp:42:19: error: mysql.h: No such file or directory
make: *** [mysql.o] Error 1
MySQL (thread-safe) disabled.
MySQL (thread-unsafe) auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o mysql.o mysql.cpp
mysql.cpp:42:19: error: mysql.h: No such file or directory
make: *** [mysql.o] Error 1
MySQL (thread-unsafe) disabled.
OCI auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o oci.o oci.cpp
oci.cpp:42:17: error: oci.h: No such file or directory
make: *** [oci.o] Error 1
OCI disabled.
ODBC auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o odbc.o odbc.cpp
odbc.cpp:45:17: error: sql.h: No such file or directory
odbc.cpp:46:20: error: sqlext.h: No such file or directory
make: *** [odbc.o] Error 1
ODBC disabled.
iODBC auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o iodbc.o iodbc.cpp
iodbc.cpp:42:17: error: sql.h: No such file or directory
iodbc.cpp:43:20: error: sqlext.h: No such file or directory
make: *** [iodbc.o] Error 1
iODBC disabled.
PostgreSQL auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o psql.o psql.cpp
psql.cpp:42:22: error: libpq-fe.h: No such file or directory
psql.cpp: In function 'int main(int, char**)':
psql.cpp:46: error: 'PQescapeBytea' was not declared in this scope
psql.cpp:47: error: 'PQunescapeBytea' was not declared in this scope
make: *** [psql.o] Error 1
PostgreSQL disabled.
SQLite2 auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o sqlite2.o sqlite2.cpp
sqlite2.cpp:42:20: error: sqlite.h: No such file or directory
make: *** [sqlite2.o] Error 1
SQLite2 disabled.
unknown SQL driver: sqlite_symbian
TDS auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o tds.o tds.cpp
tds.cpp:42:22: error: sybfront.h: No such file or directory
tds.cpp:43:19: error: sybdb.h: No such file or directory
make: *** [tds.o] Error 1
TDS disabled.
NIS auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o nis.o nis.cpp
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -Wl,-O1 -o nis nis.o     -lnsl 
NIS enabled.
Cups auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -o cups.o cups.cpp
cups.cpp:42:23: error: cups/cups.h: No such file or directory
cups.cpp: In function 'int main(int, char**)':
cups.cpp:46: error: 'cups_dest_t' was not declared in this scope
cups.cpp:46: error: 'd' was not declared in this scope
cups.cpp:47: error: 'cupsGetDests' was not declared in this scope
make: *** [cups.o] Error 1
Cups disabled.
D-Bus auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -o dbus.o dbus.cpp
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -Wl,-O1 -o dbus dbus.o     -L/lib -ldbus-1 -lpthread -lrt 
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/lib/gcc/arm-none-linux-gnueabi/4.1.2/../../../../arm-none-linux-gnueabi/bin/ld: skipping incompatible /lib/libdbus-1.so when searching for -ldbus-1
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/lib/gcc/arm-none-linux-gnueabi/4.1.2/../../../../arm-none-linux-gnueabi/bin/ld: cannot find -ldbus-1
collect2: ld returned 1 exit status
make: *** [dbus] Error 1
D-Bus disabled.
Glib auto-detection... ()
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W  -I../../../mkspecs/qws/linux-arm-imx -I. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -o glib.o glib.cpp
glib.cpp: In function 'int main(int, char**)':
glib.cpp:55: warning: 'pollfd' is used uninitialized in this function
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/bin/arm-none-linux-gnueabi-g++ -Wl,-O1 -o glib glib.o     -pthread -lgthread-2.0 -lrt -lglib-2.0 
/opt/freescale/usr/local/gcc-4.1.2-glibc-2.5-nptl-3/arm-none-linux-gnueabi/lib/gcc/arm-none-linux-gnueabi/4.1.2/../../../../arm-none-linux-gnueabi/bin/ld: cannot find -lgthread-2.0
collect2: ld returned 1 exit status
make: *** [glib] Error 1
Glib disabled.
Phonon support cannot be enabled due to functionality tests!
 Turn on verbose messaging (-v) to ./configure to see the final report.
 If you believe this message is in error you may use the continue
 switch (-continue) to ./configure to continue.

```If I do not include Phonon then the build succeeds. I think I'm missing packages but when I look in my package manager, everything appears to be there.

As you can tell I'm new to Linux so please help if you can..

---

### Post by HoeHum on 2011-11-04
bump

---

### Post by HoeHum on 2011-11-04
Is this a serious issue? Is it something I need to contact QT about?

---

### Post by HoeHum on 2011-11-08
My mistake - I moved over to Ubuntu from Fedora!

---

