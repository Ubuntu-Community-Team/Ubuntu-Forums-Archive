---
title: "Data recovery software??"
date: 2006-06-12
forum: General Help
---

### Post by CyberAngel on 2006-06-12
I accidentally removed something from my system using the "rm" command (I typed an asterisk "*" in a wrong place on the command and it removed more than I wanted to).

Is there a data recovery tool for linux like [easyrecovery]("http://www.ontrack.com/easyrecoverydatarecovery/") on windows??
How am I able to recover lost data?

Thanks in advance.

---

### Post by Rui Pais on 2006-06-12
hi,
you are in trouble...

Usually when you delete files on linux the only secure way to recover, aparently, is when you deleted on a ext2, a file system that nobody use for work :(
or a basic method that seems to work only on a single document base. Check
[this]("http://recover.sourceforge.net/unix/").

Theres are some comertial apps, like [http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm). You have to pay. Depends on the importance of your data.

I'll learn once, the hardest way, !Never type * on a line with a rm!!.

---

### Post by grte on 2006-06-12
[QUOTE=Rui Pais]I'll learn once, the hardest way, !Never type * on a line with a rm!!.[/QUOTE]

Or if you must, replace rm with ls first, just to make sure.

---

### Post by CyberAngel on 2006-06-12
I have not lost anything so useful but I am just asking just in case if I really need it on the future for some reason.

I typed "rm -rf blabla *" and I placed the asterisk to delete everything that was starting with "blabla" but accidentally I left a space between blabla and "*" so everything in that folder was removed :P

Thanks for the replys anyway!

---

