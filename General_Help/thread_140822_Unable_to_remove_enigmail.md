---
title: "Unable to remove enigmail"
date: 2006-03-07
forum: General Help
---

### Post by David Valentine on 2006-03-07
After upgrading to Thunderbird 1.5 using Automatix, I belatedly noticed that enigmail is not supported.  However, I cannot remove the now broken enigmail package--I get the following error when I type```
sudo aptitude
```and try to remove enigmail
> (Reading database ... 140851 files and directories currently installed.)
Removing mozilla-thunderbird-enigmail ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbird/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or directory
dpkg: error processing mozilla-thunderbird-enigmail (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 mozilla-thunderbird-enigmail
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Press return to continue.
Any ideas?  I've tried manually adding a dummy defaults.ini file and removing the empty installed-extensions.txt file noted in the error above, but aptitude just undoes those during the attempted removal process.

---

### Post by David Valentine on 2006-03-07
Is there any other info needed to address this, or should I have posted this in a different place?:neutral:

---

