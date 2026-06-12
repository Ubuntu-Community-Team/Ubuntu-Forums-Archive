---
title: "Only memtest86+ work when boot? Help"
date: 2010-03-10
forum: General Help
---

### Post by AlNaimi on 2010-03-10
Hi every One ....
I need your help folks
When I start ubuntu, memtest86+ work to testing memery... Nothing else show up.... just blue screen with testing...
I can't log in to ubuntu .....
I don't no how to fix that....
I tried to use live cd to edit grub, but no grub at all...
maybe because i do something wrong from this answer:
[http://superuser.com/questions/67939/blank-menu-lst-file-after-installing-ubuntu9-10](http://superuser.com/questions/67939/blank-menu-lst-file-after-installing-ubuntu9-10)

> Following is the exact answer (worked for me perfectly):

Run following command

sudo gedit /etc/default/grub

change GRUB__DEFAULT=0 to 4

And then without forget run following command :

sudo update-grub

This will update the grub.

And you are done.


Any Idea guys....

---

### Post by AlNaimi on 2010-03-10
any One?

---

### Post by egalvan on 2010-03-10
Fisrt, you changed things without knowing what was going on.
**/etc/default/grub** shows you have GRUB2 installed,
and this is edited in a different manner than the older GRUB1 (GRUB Legacy).
Too many folks treat the new one as the old one, which can cause problems, as some of the files are **not** designed to be edited by hand.

Your change made memtest the default, so it runs all the time.

You should try chaning it back to what it was,
in other words...

change GRUB__DEFAULT=4 to 0

then
find a good GRUB2 howto (hermanzone has excellent info on that)


Second, forum policy is to wait 24 hours before bumping your posts.

---

