---
title: "php5-fpm issue: expert sysadmin help please"
date: 2012-03-14
forum: General Help
---

### Post by gcaplan on 2012-03-14
Hi

ISSUE OVERVIEW

1) php-fpm is running fine on Ubuntu 12

2) I stupidly configure xdebug to run on the same port as php-fpm and try to restart php-fpm

3) I correct the misconfiguration, but now php-fpm won't start at all, even after a reboot.

4) The only diagnostics I can find are in boot.log: "Starting FastCGI server: No servers have been defined." No hits at all for this in Google. I have set up a pool which was working fine before the misconfiguration.

5) When I try removing and reinstalling php-fpm, I get "update-rc.d: warning: php5-fpm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)" This is an old bug that's supposed to be fixed. Got it on the initial install but everything worked OK.

DETAILS

1) If I run >service php5-fpm start there is a long pause, then the shell outputs "killed"

2) There is nothing in the php5-fpm log, even with log level debug, so it seems to hit the issue early in the process.

3) I've tried restarting with the xdebug config commented out, and with the webserver stopped.

4) I've tried rebooting

5) There's no orphaned pid file in /var/run, and no php-fpm processes running

6) Tried switching my pool from a port to a socket - same problem

I've run out of ideas. Any help would be more than welcome.

---

### Post by gcaplan on 2012-03-14
Discovered that xcache and xdebug are not compatible. For some reason, after trying to run them together php-fpm wouldn't start even though I had disabled xdebug. Disabling both xcache and xdebug has fixed the issue. Now I have to figure out how to get xcache working again...

---

