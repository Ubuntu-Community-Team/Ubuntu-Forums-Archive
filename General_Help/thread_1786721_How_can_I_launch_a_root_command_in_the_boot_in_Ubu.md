---
title: "How can I launch a root command in the boot in Ubuntu 11.04?"
date: 2011-06-20
forum: General Help
---

### Post by marquinos on 2011-06-20
Hi! In a computer, the brightness can't be changed with the *fn* key (and the brightness starts at 100%) :S

I can set the brightness with this command from a shell:
*sudo setpci -s 00:02.0 F4.B=25*


In Ubuntu 10.04 worked set this command in [I]/etc/rc.local
[/I]But in Ubuntu 11.04 I did this, but it didn't work.

In which file can I set a root command in the boot **in Ubuntu 11.04**? 

Thanks in advance!

---

### Post by gmargo on 2011-06-20
Check the permissions on /etc/rc.local - the file must be executable.

---

### Post by galvatron408 on 2011-06-20
you probably don't realize what sudo is meant to do. so, don't use sudo and you'll be fine.

---

### Post by marquinos on 2011-06-20
Hi! The energy manager works for me :$ I didn't remember it!
Thanks very much and sorry!

---

