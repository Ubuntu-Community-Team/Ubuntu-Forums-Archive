---
title: "WOL should I do?"
date: 2010-11-03
forum: General Help
---

### Post by JustGus on 2010-11-03
I've just had to do a clean install of Lucid and can't seem to get my WOL working (it was before).

I've written a script, enabled it through the terminal, but when I try to assign it I get the following. I've followed the link that's quoted but can't make head or tail of what I should do next:
> update-rc.d -f wol.sh defaults
update-rc.d: warning: /etc/init.d/wol.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/wol.sh already exist.
Died at /usr/sbin/update-rc.d line 57.

I've checked line 57, which says:
>     open(FILE, ">", "$archive/${script}.new") || die;
Can anyone help clarify why this isn't working?
Cheers

---

### Post by JustGus on 2010-11-05
Found the answer here.  Wonderfully well done instructions!
[http://ubuntuforums.org/showthread.php?t=234588]("http://ubuntuforums.org/showthread.php?t=234588")

---

