---
title: "Preventing php from timing out on Ubuntu server."
date: 2010-05-04
forum: General Help
---

### Post by itsols on 2010-05-04
I am running a PHP application that is on Ubuntu 8.04 server.

If the user is idle for a while, his session gets logged out. Is there a way on Ubuntu to prevent this? On Windows it was a setting in drive:\wamp...

Sorry if this is not the right place but I couldn't find a better location to post this.

Thanks for any advice.

---

### Post by gzarkadas on 2010-05-04
The PHP settings are all in php.ini (which for ubuntu 9.10 is in /etc/php5/apache2/php.ini). For 8.04, I suppose the versions are different, so make an `ls /etc/php*' to find the right directory.

What you want will most probably be at the section with title `[Session]'  (I bet to be the line: `session.cookie_lifetime'). Check its current value and modify accordingly. The related php docs are [here]("http://php.net/manual/en/session.configuration.php#ini.session.cookie-lifetime").

---

### Post by itsols on 2010-05-04
Thank you gzarkadas!

That was the same path and version I found on my system.

BTW, the lie to change was:
> session.gc_maxlifetime = 1440

Thank you for your tip!

---

### Post by gzarkadas on 2010-05-05
Glad I could be of help :). And thanks for the information; I 'll keep it for reference.

---

