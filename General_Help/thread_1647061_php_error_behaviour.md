---
title: "php error behaviour"
date: 2010-12-16
forum: General Help
---

### Post by RichLouth on 2010-12-16
I've got code that *should* throw an "Warning: Cannot modify header information - headers already sent" error.

e.g.
var_dump('this should cause an error');
header('Location: index.php');

Just to be clear, I *want* to see it throw this error. I was working in 9.04 with php 5.2 up until recently so I assume it's got something to do with me upgrading to 10.10 or some change in 5.3.

I've already modified /etc/php5/apache2/php.ini and set:
error_reporting = E_ALL | E_STRICT
display_errors = on
and reset the system for these changes to take effect.

What else am I missing?

Thanks

---

### Post by RichLouth on 2010-12-16
I've managed to answer my own question:

As explained here: [http://www.wampserver.com/phorum/read.php?2,42142]("http://www.wampserver.com/phorum/read.php?2,42142")

In /etc/php5/apache2/php.ini Ubuntu is setting:

output_buffering = 4096

When the default value is supposed to be:

output_buffering = Off

It's frustrating that Ubuntu has set php.ini in this way. In my opinion the default for Ubuntu should be to have:

error_reporting = E_ALL | E_STRICT
output_buffering = Off

I shouldn't have to configure php to get a development system running. Whereas if I were setting up a production server reviewing php.ini would be one of the many necessary steps.

---

