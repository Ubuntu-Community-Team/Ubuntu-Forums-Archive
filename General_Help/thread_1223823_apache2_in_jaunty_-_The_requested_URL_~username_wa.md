---
title: "apache2 in jaunty - The requested URL /~username was not found on this server"
date: 2009-07-26
forum: General Help
---

### Post by chicoperico on 2009-07-26
hello all,

even though i have been a linux user for more than 10 years and an ubuntu user for the last few years, my latest update from hardy to jaunty was a very thorny issue.

as i am working a lot with my internal apache2 server, i was less than delighted when an attempt to adress my public_html folder was answered by an error 404 message:
The requested URL /~my_user_name was not found on this server

after an hour's or more searching on ubuntuforums i found the solution at
[http://www.backports.ubuntuforums.org/showthread.php?t=1083439](http://www.backports.ubuntuforums.org/showthread.php?t=1083439)

it is as easy as this:
sudo a2enmod userdir


i hope this saves others the same trouble!
why did this work under hardy, but did not under jaunty?

best regards,
Rainer

---

