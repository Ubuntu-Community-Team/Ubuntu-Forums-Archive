---
title: "Compiling PHP 5.3 on Ubuntu 9.10"
date: 2010-01-27
forum: General Help
---

### Post by mysticav on 2010-01-27
I'm trying to build php 5.3 on Ubuntu. I have installed
apache2-threaded-dev and used the following configure settings:

./configure --with-apxs2=/usr/bin/apxs2

There are no errors and I get the "thank you for using PHP" message.

But running make starts building some files until it fails with the
following output:

ext/sqlite3/libsqlite/sqlite3.o: In function `memset':
/usr/include/bits/string3.h:82: warning: memset used with constant zero length parameter; this could be due to transposed parameters
ext/standard/.libs/info.o: In function `php_info_print_table_header':
/root/Downloads/php/php-5.3.0/ext/standard/info.c:1071: undefined reference to `ts_resource_ex'
ext/standard/.libs/info.o: In function `php_info_write_wrapper':
/root/Downloads/php/php-5.3.0/ext/standard/info.c:80: undefined reference to `ts_resource_ex'
ext/standard/.libs/info.o: In function `php_info_print_table_row_internal':
/root/Downloads/php/php-5.3.0/ext/standard/info.c:1115: undefined reference to `ts_resource_ex'
ext/standard/.libs/info.o: In function `php_print_gpcse_array':
/root/Downloads/php/php-5.3.0/ext/standard/info.c:150: undefined reference to `executor_globals_id'
ext/standard/.libs/info.o: In function `php_print_info':
/root/Downloads/php/php-5.3.0/ext/standard/info.c:939: undefined reference to `executor_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:942: undefined reference to `executor_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:945: undefined reference to `executor_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:948: undefined reference to `executor_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:870: undefined reference to `sapi_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:644: undefined reference to `sapi_globals_id'
/root/Downloads/php/php-5.3.0/ext/standard/info.c:849: undefined reference to `sapi_globals_id'
collect2: ld returned 1 exit status
make: *** [sapi/cli/php] Error 1


Are those undefined references causing the problem ?
Can somebody give me at least a clue ?

Is there any PHP 5.3 (SAPI Apache2handler)  .deb package for Ubuntu 9.10 ?

I have gone so far  trying to make my own compilation but I can't fix this.

Please help.

---

