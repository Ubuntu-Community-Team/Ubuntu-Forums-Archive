---
title: "All commands run that prompt for Y or N to continue"
date: 2009-09-25
forum: General Help
---

### Post by gibbs_wesley@bah.com on 2009-09-25
When your running something like the following:

sudo su -
apt-get upgrade

you will be later promted for Y or N...

is there some optional paramter I could type after the apt-get upgrade 
command so that it would not prompt me for the Y or N at a later time?

Thanks in advance,
Wes

---

### Post by ecmatter on 2009-09-25
From the man page for apt-get:

> 
Options
-y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install a unauthenticated
           package or removing an essential package occurs then apt-get will
           abort.


---

