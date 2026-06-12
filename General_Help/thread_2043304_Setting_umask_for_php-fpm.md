---
title: "Setting umask for php-fpm"
date: 2012-08-16
forum: General Help
---

### Post by Versusnja on 2012-08-16
Hi everybody.

I can't set umask for the php-fpm.
Every time when I write a file to disk is has permissions 600. 

I found several approaches to setting umask and different people say it works, but none worked for me. Here are the options for editing /etc/init.d/php-fpm

Option 1:
> Set 
[FONT="Courier New"][COLOR="DarkRed"]**umask 022**[/COLOR][/FONT]
in the beginning of /etc/init.d/php-fpm

Option 2:
> 
Start php-fpm with --umask 022 parameter:
[FONT="Courier New"]start-stop-daemon --start --quiet [COLOR="DarkRed"]**--umask 022**[/COLOR] --pidfile $PIDFILE --exec $DAEMON -- \
                $DAEMON_ARGS 2>/dev/null \
                || return 2[/FONT]



Option 3:
Setting umask somewhere in /etc/profile or other places.
That I didn't try as the previous one should definitely work.

So, the question is why the option 2 doesn't affect umask of php-fpm?

Are there other options for setting umask for php-fpm except for PHP umask() function, which I'm trying to avoid?

Ubuntu 12.04

---

