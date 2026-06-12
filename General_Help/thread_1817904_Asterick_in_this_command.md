---
title: "Asterick in this command"
date: 2011-08-03
forum: General Help
---

### Post by tech291083 on 2011-08-03
Hi,

If I type the following command with an asterick at the end will it download all the required dependencies and software packages for MySQL  such as MySQL Administrator, Query Browser etc. ?

```
sudo apt-get install mysql*
```

or do I need to use something like this mentioning every individual component.

```
sudo apt-get install mysql-server mysql-client 
```

Thanks

---

### Post by tech291083 on 2011-08-05
Please help me out, thanks

---

### Post by Wim Sturkenboom on 2011-08-05
from man apt-get
> 
           If no package matches the given expression and the expression contains one of '.', '?' or '*' then it is assumed to be a
           POSIX regular expression, and it is applied to all package names in the database. Any matches are then installed (or
           removed). Note that matching is done by substring so 'lo.*' matches 'how-lo' and 'lowest'. If this is undesired, anchor the
           regular expression with a '^' or '$' character, or create a more specific regular expression.
And please note the last sentence.

PS never used it that way ! So use at own risk ;)

---

### Post by Furball588 on 2011-08-05
No doubt...

You might get better milage by going with apt-cache  search mysql* and just seeing what's out there.

---

### Post by tech291083 on 2011-08-05
Thanks guys,

I vaguely remember that I used to use an asterick * in Fedora terminal as sudo to download all the related packges/dependencies instead of typing like yum install php-xyz, I could be mistaken though.

---

