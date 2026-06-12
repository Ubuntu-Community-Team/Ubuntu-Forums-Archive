---
title: "VM Swappiness?"
date: 2010-09-21
forum: General Help
---

### Post by baracuda68 on 2010-09-21
Hi
In nearly all postings about adjusting Swappiness of drives, the tweak ( something like vm.swappiness = 10) is usually put into
/etc/sysctl.conf. Can anyone explain to me why it is in THIS file?
All other settings in this file pertain to networking/Internet settings, nothing to do with virtual memory, or swapping...
Please elaborate, if possible.
Thanks.:???:

---

### Post by bodhi.zazen on 2010-09-21
See the links I posted here :

[http://ubuntuforums.org/showpost.php?p=9872966&postcount=3](http://ubuntuforums.org/showpost.php?p=9872966&postcount=3)

Especially 

[http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

sysctl.conf is a configuration fole for the linux kernel and although you most often see people tuning networking parameters, you can tune other parameters as well.

[http://manpages.ubuntu.com/manpages/lucid/en/man5/sysctl.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/sysctl.conf.5.html)

[http://manpages.ubuntu.com/manpages/lucid/en/man8/sysctl.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/sysctl.8.html)

[http://www.linux.com/archive/articles/146599](http://www.linux.com/archive/articles/146599)

[http://www.linuxjournal.com/article/2365](http://www.linuxjournal.com/article/2365)

---

### Post by baracuda68 on 2010-09-21
Thanks a bunch for clearing that up for me, bodhi. A big help!! :)

---

### Post by bodhi.zazen on 2010-09-21
> **baracuda68 said:**
> Thanks a bunch for clearing that up for me, bodhi. A big help!! :)

You are most welcome.

---

