---
title: "Recover deleted files (newbie mistake)"
date: 2010-04-26
forum: General Help
---

### Post by Luminaric on 2010-04-26
I managed to delete part of my /var directory today as I was trying to restore my web site data.  I used the rm command.  However, I think I found the deleted files in the /proc directory.  When I enter the following:
ls -ltr -R | grep /var/

I get something like:

1-wx------ 1 root root 64 2010-04-26 16:07 2 -> /var/log/apache2/error.log (deleted)

Question.  Can I use this output to cp the deleted files to another drive?  If so how?  I'm not all that good with piping which is what I suspect will need to be used to do this.

Thanks,
Luminaric

---

### Post by dannyboy79 on 2010-04-26
hate to break it to ya but if you used rm and you didn't stop it mid-delete, your files are gone. not sure what you found in /proc/

all about the proc directory
[http://www.linux.com/archive/feature/126718](http://www.linux.com/archive/feature/126718)

---

