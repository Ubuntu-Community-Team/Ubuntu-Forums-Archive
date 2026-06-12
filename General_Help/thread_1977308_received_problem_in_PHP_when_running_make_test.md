---
title: "received problem in PHP when running make test"
date: 2012-05-09
forum: General Help
---

### Post by associates on 2012-05-09
Hi,

I was wondering if I could get some help with PHP installation from the source rather than from the Ubuntu Server 12.04 package.

I have run both ./configure and make with no errors messages. However, when I run make test, I got the following error messages that requires me to email to the QA PHP. 

Here is my ./configure detail:
./configure --prefix=/usr/local/php5 --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-bz2 --with-zlib --enable-zip --enable-mbstring --with-mcrypt

The error messages received is as follows:

=====================================================================
EXPECTED FAILED TEST SUMMARY
---------------------------------------------------------------------
Test open_basedir configuration [tests/security/open_basedir_linkinfo.phpt]  XFAIL REASON: BUG: open_basedir cannot delete symlink to prohibited file. See also
bugs 48111 and 52176.
Inconsistencies when accessing protected members [Zend/tests/access_modifiers_008.phpt]  XFAIL REASON: Discussion: [http://marc.info/?l=php-internals&m=120221184420957&w=2](http://marc.info/?l=php-internals&m=120221184420957&w=2)
Inconsistencies when accessing protected members - 2 [Zend/tests/access_modifiers_009.phpt]  XFAIL REASON: Discussion: [http://marc.info/?l=php-internals&m=120221184420957&w=2](http://marc.info/?l=php-internals&m=120221184420957&w=2)
Bug #48770 (call_user_func_array() fails to call parent from inheriting class) [Zend/tests/bug48770.phpt]  XFAIL REASON: See Bug #48770
Bug #48770 (call_user_func_array() fails to call parent from inheriting class) [Zend/tests/bug48770_2.phpt]  XFAIL REASON: See Bug #48770
Bug #48770 (call_user_func_array() fails to call parent from inheriting class) [Zend/tests/bug48770_3.phpt]  XFAIL REASON: See Bug #48770
Initial value of static var in method depends on the include time of the class definition [Zend/tests/method_static_var.phpt]  XFAIL REASON: Maybe not a bug
DateTime::add() -- fall type2 type3 [ext/date/tests/DateTime_add-fall-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::add() -- fall type3 type2 [ext/date/tests/DateTime_add-fall-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::add() -- fall type3 type3 [ext/date/tests/DateTime_add-fall-type3-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::add() -- spring type2 type3 [ext/date/tests/DateTime_add-spring-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::add() -- spring type3 type2 [ext/date/tests/DateTime_add-spring-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::add() -- spring type3 type3 [ext/date/tests/DateTime_add-spring-type3-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- fall type2 type3 [ext/date/tests/DateTime_diff-fall-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- fall type3 type2 [ext/date/tests/DateTime_diff-fall-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- fall type3 type3 [ext/date/tests/DateTime_diff-fall-type3-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- spring type2 type3 [ext/date/tests/DateTime_diff-spring-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- spring type3 type2 [ext/date/tests/DateTime_diff-spring-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::diff() -- spring type3 type3 [ext/date/tests/DateTime_diff-spring-type3-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- fall type2 type3 [ext/date/tests/DateTime_sub-fall-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- fall type3 type2 [ext/date/tests/DateTime_sub-fall-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- fall type3 type3 [ext/date/tests/DateTime_sub-fall-type3-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- spring type2 type3 [ext/date/tests/DateTime_sub-spring-type2-type3.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- spring type3 type2 [ext/date/tests/DateTime_sub-spring-type3-type2.phpt]  XFAIL REASON: Various bugs exist
DateTime::sub() -- spring type3 type3 [ext/date/tests/DateTime_sub-spring-type3-type3.phpt]  XFAIL REASON: Various bugs exist
Bug #53437 (Crash when using unserialized DatePeriod instance) [ext/date/tests/bug53437.phpt]  XFAIL REASON: Bug #53437 Not fixed yet
RFC: DateTime and Daylight Saving Time Transitions (zone type 3) [ext/date/tests/rfc-datetime_and_daylight_saving_time-type3.phpt]  XFAIL REASON: RFC not implemented yet
Bug #42718 (unsafe_raw filter not applied when configured as default filter) [ext/filter/tests/bug42718.phpt]  XFAIL REASON: FILTER_UNSAFE_RAW not applied when configured as default filter, even with flags
Optional long parameter might be null [ext/mbstring/tests/mb_str_functions_opt-parameter.phpt]  XFAIL REASON: mb functions fail to allow null instead of actual value
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) [ext/session/tests/bug60634.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) - fatal error in write during exec [ext/session/tests/bug60634_error_1.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) - exception in write during exec [ext/session/tests/bug60634_error_2.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) - fatal error in write after exec [ext/session/tests/bug60634_error_3.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) - exception in write after exec [ext/session/tests/bug60634_error_4.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #60634 (Segmentation fault when trying to die() in SessionHandler::write()) - fatal error in close during exec [ext/session/tests/bug60634_error_5.phpt]  XFAIL REASON: Long term low priority bug, working on it
Bug #45712 (NaN/INF comparison) [ext/standard/tests/math/bug45712.phpt]  XFAIL REASON: Bug 45712 not fixed yet.
=====================================================================

=====================================================================
FAILED TEST SUMMARY
---------------------------------------------------------------------
GC 029: GC and destructors [Zend/tests/gc_029.phpt]
test for mbstring script_encoding for flex unsafe encoding (Shift_JIS) [Zend/tests/multibyte/multibyte_encoding_004.phpt]
encoding conversion from script encoding into internal encoding [Zend/tests/multibyte/multibyte_encoding_005.phpt]
Test 7: DTD tests [ext/dom/tests/dom007.phpt]
Phar: phpinfo display 1 [ext/phar/tests/phpinfo_001.phpt]
Phar: phpinfo display 2 [ext/phar/tests/phpinfo_002.phpt]
Phar: phpinfo display 4 [ext/phar/tests/phpinfo_004.phpt]
Test debug_zval_dump() function : working on objects [ext/standard/tests/general_functions/debug_zval_dump_o.phpt]
Bug#60106 (stream_socket_server silently truncates long unix socket paths) [ext/standard/tests/streams/bug60106.phpt]
=====================================================================

You may have found a problem in PHP.
This report can be automatically sent to the PHP QA team at
[http://qa.php.net/reports](http://qa.php.net/reports) and [http://news.php.net/php.qa.reports](http://news.php.net/php.qa.reports)
This gives us a better understanding of PHP's behavior.
If you don't want to send the report immediately you can choose
option "s" to save it.	You can then email it to [email]qa-reports@lists.php.net[/email] later.


I wonder if there is a workaround to this problem. 

Any help would be greatly appreciated. Thank you

---

