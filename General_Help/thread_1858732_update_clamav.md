---
title: "update clamav"
date: 2011-10-12
forum: General Help
---

### Post by brad1138 on 2011-10-12
How do you update Clamav? I found this tutorial, but I don't understand it.

 [http://internet-security-tips.com/blog/2010/how-to-update-clamav-debian-centos5/](http://internet-security-tips.com/blog/2010/how-to-update-clamav-debian-centos5/) 


One problem with Linux command line tutorials it they assume you know Linux inside and out. Example:

[I]"Last step is to manually update the virus signature and verify the clamav log to see if there is any warning message.

/usr/local/bin/freshclam -l /var/log/clamav-update.log"[/I]


It doesn't tell you what to do with that line (/usr...) where to enter it, if you figure out you should enter it into terminal, in what fold or location? I copied the last line into Terminal and it didn't work. They give no directions beyond that. 

Anyway, sorry, just a bit frustrated. 

Brad

---

### Post by wildmanne39 on 2011-10-12
Hi, type paste this into the terminal:
```
sudo freshclam
```
Then type your password and hit enter.
Thank you

---

### Post by brad1138 on 2011-10-12
> **wildmanne39 said:**
> Hi, type paste this into the terminal:
```
sudo freshclam
```
Then type your password and hit enter.
Thank you

Thank you, that is so simple, why didn't the web page tutorial just say that?

Thanks again,
Brad

---

### Post by wildmanne39 on 2011-10-12
Hi, go into the forums security thread and you will learn a lot about security and installing applications for security.

But take it a little at a time, some of it can be complicated for a new person.
Thank you

---

