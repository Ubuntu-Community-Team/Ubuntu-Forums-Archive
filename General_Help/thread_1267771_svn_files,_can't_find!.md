---
title: "svn files, can't find!"
date: 2009-09-16
forum: General Help
---

### Post by dchurch24 on 2009-09-16
Hi all,

I set up a SVN server on my Ubuntu server, and after a few struggles it works fine.

I can check in and out from anywhere on my lan etc... and all is fine.

I wanted to add the svn folder into my backup script that copies files over to an external SAN, but when I browse to the svn folder, it is empty.

I uploaded a file called "settings.xml" and then did a search of the whole drive:

$ sudo find / -name 'settings.xml'

...in an attempt to find where it had uploaded it to, but the find doesn't return it.

If I check that project out on a 'virgin' machine, sure enough, the settings.xml file is where it should be in the working directory.

Does anyone have any ideas where it might be keeping my code so that I can add it into my backup?

---

