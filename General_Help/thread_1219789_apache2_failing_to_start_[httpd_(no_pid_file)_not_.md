---
title: "apache2 failing to start [httpd (no pid file) not running]"
date: 2009-07-22
forum: General Help
---

### Post by wlan-11g on 2009-07-22
Apache2 failing to start..

I recently did an apt-get upgrade, installed TWiki ([http://www.twiki.org](http://www.twiki.org)), these are the only two things I can think of which may have caused this crash. 

Below is an ouput from /var/log/apache2/error.log

Sun Jul 19 21:34:09 2009] [error] Insecure dependency in chdir while running with -T switch at /usr/share/perl/5.8/File/Path.pm line 178.\nCompilation failed in require at (eval 5) line 1.\n
[Sun Jul 19 21:34:09 2009] [error] Can't load Perl file: /usr/share/request-tracker3.4/libexec/webmux.pl for server 127.0.1.1:0, exiting...

Any help would be great!

Thanks

---

