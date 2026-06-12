---
title: "package manager/apache2 ques"
date: 2010-05-22
forum: General Help
---

### Post by Duckslammer on 2010-05-22
I used "apt-get remove" to remove my apache2 installation and then I foolishly deleted everything under /etc/apache2 thinking a reinstall later would put them back.  Wrong.  Then I thought if I could remove all traces of apache from my system, "apt-get install" would recreate everything from scratch, so I used "dpkg -P".  Wrong again.  Can someone tell me   (a) Is there a way to completely wipe ALL traces of apache2 from my system so I can completely reinstall everything?  Can I manually edit whatever database the package manager uses to make it think apache2 with its parts and pieces is yet to be installed - would that do it?  -or-  (b) How can I acquire the missing /etc/apache2 files?  These include not only the config files but also the loadable modules.  Might the remove have taken out something else I don't yet know about and also need to replace?

---

### Post by albinootje on 2010-05-22
> **Duckslammer said:**
> I used "apt-get remove" to remove my apache2 installation and then I foolishly deleted everything under /etc/apache2 thinking a reinstall later would put them back.  Wrong.  Then I thought if I could remove all traces of apache from my system, "apt-get install" would recreate everything from scratch, so I used "dpkg -P".  Wrong again. 

You can use ```
dpkg -l|grep apache
``` to see whether any apache related packages still have a "rc" label at the left.
That means that the package is removed but the configuration isn't removed.
In case of the apache2 packages which still have "rc", dpkg -P should work to purge the configuration as well.

Note that you might have to remove the apache2.2 common and apache mod, and php packages if you really want to start from scratch with apache2.

And for the future, use ```
sudo apt-get purge apache2* apache2-*
``` for this. (Note that this won't work if you have already used apt-get remove on them, where they would have the "rc" label)

GL!

---

### Post by Duckslammer on 2010-05-22
I did ```
dpkg -l &quot;*apache*&quot;
```  Then I reinstalled the likely suspects, apache2.2-common and apache2-util  That got me /etc/apache2 back. 

And a question about posts: is there some way to keep the forum from stripping out linefeeds?  Do I have to manually type bbcodes for every linebreak?  Never saw that before as the default on a bbs.

---

### Post by Duckslammer on 2010-05-22
Ok, followed your instructions and the whole thing reloaded.  Thanks!

---

