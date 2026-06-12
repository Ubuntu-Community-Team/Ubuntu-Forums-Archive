---
title: "Localhost Issues"
date: 2011-06-16
forum: General Help
---

### Post by ptmuldoon on 2011-06-16
I'm having a headache of time trying to understand what happened to my webserver.

I'm running ubuntu server 10.04 as well, if anyone feels this should be moved to the server subforums.

I think this 'broke' after recently upgrading all my packages.

If I try to access localhost.... I'm told the webpage is not available.

If type the PC's address of 192.168.xx.xx, I get the "it Works!" page.

But I can not access phpmyadmin either when using the IP address of 192.168.xx.xx/phpmyadmin.   Nor can I hit any other info as a phpinfo.php file or other sites/scripts.

I did check my hosts file and is shows 127.0.0.1 locahost is shown.

Now, what's a little stranger is that that I can type localhost:1000 and access WebMin on the machine

and I can also access localhost:49152 to get to mediatomb.

so is it possible its just something with port 80?  But why would I connect 192.168.xx.xx to the defaut 'it works!' page, and not via localhost?

---

### Post by ptmuldoon on 2011-06-16
Just one to post back that following these instructions to a complete removal of apache2, including the config files, and than a reinstall was able to correct things.

[http://ubuntuforums.org/showthread.php?t=1071947&page=2](http://ubuntuforums.org/showthread.php?t=1071947&page=2)

---

