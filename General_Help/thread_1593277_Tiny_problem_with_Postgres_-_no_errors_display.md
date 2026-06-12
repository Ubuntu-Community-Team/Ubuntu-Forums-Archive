---
title: "Tiny problem with Postgres - no errors display"
date: 2010-10-11
forum: General Help
---

### Post by madelus on 2010-10-11
I believe that is quite simple problem, but just can't find it anywhere.

I've installed Maverick today, and probably missed some configuration in my php.ini or something. The problem is:
**Postgres errors are not displayed in browser**.


1. When php finds postgres error it just gives blank page, processing is stopped.
But, on the other hand, I can see errors typing in console:
tail -f /var/log/apache2/error.log

2. I have errors reporting in php.ini set to:
error_reporting = E_ALL | E_STRICT & ~E_DEPRECATED

3. The pgsql extension is enabled in php.ini
extension=pgsql.so
and web-services i build work good, and are able to properly connect and use DB. Only problem is displaying errors.

Can someone please remind me where the solution was?

---

### Post by agwells on 2010-10-11
I think I experienced the same thing. Specifically, what I found was that after upgrading to Maverick, if I use the PHP function **pg_query()** to run a Postgres query that results in an error (like "select * from no_such_table"), the PHP script dies at that point and PHP returns no output of any kind. On the web browser side, this results in the user either getting a blank page, or a pop-up asking them to save the current page as a file.

I suspect it's a bug in Maverick, rather than a configuration issue, because I also did a clean install of Maverick in a virtual machine and it had the same issue.

I notice there's a PHP bug describing similar behavior, but it reports the problem as resolved: [http://bugs.php.net/bug.php?id=52682](http://bugs.php.net/bug.php?id=52682)

I've worked around it for the time being by reverting to the php5 packages for Lucid. Hopefully someone out there has a better solution? :)

---

### Post by madelus on 2010-10-13
Well, it doesn't look good, from what you say. 

I wouldn't tell i have a workaround, but instead changing libraries for old ones, for now at least, i just tail the log file in geany console. It is not that bad solution cause i can see both code and error information in one place, without moving windows or something like that.

Anyway, thanks for response and lets hope there will be some fix for it sometime.

---

### Post by agwells on 2010-10-18
This problem is fixed in the latest version of php5-pgqsl in the "maverick-proposed" repository. See : [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/660227](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/660227)

---

### Post by madelus on 2010-10-19
Works great! Thank you!

---

