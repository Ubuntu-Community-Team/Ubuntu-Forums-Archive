---
title: "Alternative to Ditto"
date: 2012-09-13
forum: General Help
---

### Post by sivacrom on 2012-09-13
Hello!  I'm in a bit of a pickle porting over a shell script from OS X to Linux.  Specifically, I used the ditto command while looping through a list of full file paths.  For instance, if my list were;

/etc/bind/zones/db.domain.private
/etc/warning
/etc/cron.daily/script.sh

I could ditto each one to a backup directory like so;

ditto /etc/bind/zones/db.domain.private ~/backup/etc/bind/zones/db.domain.private
ditto /etc/warning ~/backup/etc/warning
ditto /etc/cron.daily/script.sh ~/backup/etc/cron.daily/script.sh

And, there you have it, I'd have a backup of all the files in my filesystem with with their entire enclosing paths copied over, too.  No complaints of directories not existing, or anything like that.  As far as I can tell, Linux hasn't got a ditto, so I have tried cp with a few tags and I just can't seem to reproduce this.  Can anyone give me a tip for proper syntax?  Or an alternative command that could accomplish the same thing?

Thanks!

---

### Post by papibe on 2012-09-13
Hi sivacrom.

Take a look at [rsync]("https://help.ubuntu.com/community/rsync").

Let us know how it goes.
Regards.

---

### Post by sivacrom on 2012-09-13
I know rsync well.  I'm using it in more than one part of the same script, as a matter of fact.

But I found the answer I wanted, and it was this;

cp -Rp --parents  /etc/bind/zones/db.domain.private ~/backup
cp -Rp --parents  /etc/warning ~/backup
cp -Rp --parents  /etc/cron.daily/script.sh ~/backup

My Google fu is better than I gave myself credit for.  ;)

Sorry everyone!

---

