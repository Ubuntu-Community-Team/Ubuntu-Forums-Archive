---
title: "cron and local mail"
date: 2010-01-13
forum: General Help
---

### Post by jessel on 2010-01-13
Hi,

I'm looking for advice on whether or not local mail is the best way to get feedback from cron jobs. I am asking this question regarding personal desktop computers running Ubuntu.

Lately I have become more concerned with protecting against data loss. I have implemented "rsnapshot" and a disk copy scheme as outlined in [http://www.jwz.org/doc/backups.html](http://www.jwz.org/doc/backups.html) (basically you use a second drive as a copy of the primary drive). Now, as you can see you are copying a lot of files and the way my cron jobs show up in the log files I can only tell if there was an error or not, knowing the warnings is critical. Obviously I can just look at my filesystem and check if files are present, but if a file was skipped with a warning I really want to know, I doubt I'll figure it out by browing the directory tree.

Ubuntu does not come with local mail system by default (at least not in Hardy or Jaunty) and I feel that this is with good reason however detailed output from cron jobs are useful. Installing local mail is  easy using synaptic (though I still recall having some major problems a few years back). On the other hand, I feel like its overkill and really just a waste of reseources.

OK, so I did install sendmail and it works fine. But I'm wondering if there is another way to get feedback from cron jobs. I figure there probably is a better way to do what I want I just don't know about it!

I would think the dbus messaging system could be used, but I don't think this would be an effective solution. The reason is that the message will be essentially lost if another user is using the computer and unless the message is written to a file I won't be able to google the error message. Also, if I just write the output to a file I will not check the file everyday...

Thanks in advance.

---

### Post by i.r.id10t on 2010-01-13
> **jessel said:**
> Hi,

I'm looking for advice on whether or not local mail is the best way to get feedback from cron jobs. I am asking this question regarding personal desktop computers running Ubuntu.

Lately I have become more concerned with protecting against data loss. I have implemented "rsnapshot" and a disk copy scheme as outlined in [http://www.jwz.org/doc/backups.html](http://www.jwz.org/doc/backups.html) (basically you use a second drive as a copy of the primary drive). Now, as you can see you are copying a lot of files and the way my cron jobs show up in the log files I can only tell if there was an error or not, knowing the warnings is critical. Obviously I can just look at my filesystem and check if files are present, but if a file was skipped with a warning I really want to know, I doubt I'll figure it out by browing the directory tree.

Ubuntu does not come with local mail system by default (at least not in Hardy or Jaunty) and I feel that this is with good reason however detailed output from cron jobs are useful. Installing local mail is  easy using synaptic (though I still recall having some major problems a few years back). On the other hand, I feel like its overkill and really just a waste of reseources.

OK, so I did install sendmail and it works fine. But I'm wondering if there is another way to get feedback from cron jobs. I figure there probably is a better way to do what I want I just don't know about it!

I would think the dbus messaging system could be used, but I don't think this would be an effective solution. The reason is that the message will be essentially lost if another user is using the computer and unless the message is written to a file I won't be able to google the error message. Also, if I just write the output to a file I will not check the file everyday...

Thanks in advance.

Redirect output to a file... either both stdout and stderr to one file or separate files for each.

---

### Post by jessel on 2010-01-13
Thanks for the reply.

OK, I can redirect to a file. I just feel like I need to get alerted somehow when the error log get written to... The fact is, I will monitor the file for a while and at some point I'll stop. At some point I will need my backup, I just want to make sure its there when I need it.

---

