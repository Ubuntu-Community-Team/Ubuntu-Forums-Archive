---
title: "PhpPgadmin fails with multiple messages"
date: 2011-09-20
forum: General Help
---

### Post by JimGvo on 2011-09-20
I searched for some of the error messages but didn't really find a solution.  Seems the version of Php and PhPPgadmin might be incompatable.  How do I fix it?

Thanks,
Jim.

[https://localhost/phppgadmin/](https://localhost/phppgadmin/) gives me 

> Deprecated: Assigning the return value of new by reference is deprecated in /usr/share/phppgadmin/classes/Misc.php on line 342

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /usr/share/phppgadmin/classes/Misc.php:342) in /usr/share/phppgadmin/libraries/lib.inc.php on line 56

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /usr/share/phppgadmin/classes/Misc.php:342) in /usr/share/phppgadmin/libraries/lib.inc.php on line 56

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/phppgadmin/classes/Misc.php:342) in /usr/share/phppgadmin/classes/Misc.php on line 359

---

