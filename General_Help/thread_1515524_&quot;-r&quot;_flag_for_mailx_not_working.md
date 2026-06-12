---
title: "&quot;-r&quot; flag for mailx not working?"
date: 2010-06-22
forum: General Help
---

### Post by Minnesota_Miracle_Man on 2010-06-22
Hey everyone.

I recently set up an email server at work on a ubuntu box, running exim4. Everything seems to be working fine, but when I try to change the "from" header in the message, its not letting me. 

I wanted to send a message from the root user as "admin". 

I assumed this would be easy as:

```
 mailx -r admin recepientname 
```

but for some reason the mailx program is claiming that "-r" is not a legitimate tag, when I try it tells me: 

```
 mail: invalid option -- r
usage: mail [-eIinv] [-a header] [-b bcc-addr] [-c cc-addr] [-s subject] to-addr ...
            [-- sendmail-options ...]
       mail [-eIiNnv] -f [name]
       mail [-eIiNnv] [-u user]

```

I'm pretty new to Ubuntu and Unix in general, so beginner-level help would be greatly appreciated!

---

### Post by gmargo on 2010-06-22
There are a several packages that provide the **mailx** command.  For 10.04 Lucid:
```

bsd-mailx - simple mail user agent
heirloom-mailx - feature-rich BSD mail(1)
mailutils - GNU mailutils utilities for handling mail

```You probably have the **bsd-mailx** package installed, which does not support the -r option.  Replace it with the **heirloom-mailx** package which does support the -r option.  (Or use sendmail -r (or -f) directly.)

---

