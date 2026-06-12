---
title: "gdm 3 user list security bug"
date: 2012-05-28
forum: General Help
---

### Post by goneskiing on 2012-05-28
is there any way to eliminate gdm 3 or get rid of the user list ?

having user names listed on gdm 3 is a major security issue - it takes away 1 level of security (knowing user names) which means an exponential difference in hacking combinations

thru lots of searching, there seems no way to eliminate usernames from showing - this code must be really buried. 

and there seems to be lots of people complaining about this with no one able to resolve it

And whoever put this into gdm 3 should be kicked off the committer list for intentionally diminishing security plus intentionally making it so nearly impossible to correct.  Plus, they have wasted lots of programmers valuable time, searching in vain to correct this.

---

### Post by cortman on 2012-05-28
Ubuntu doesn't even use GDM...
How about you switch to LightDM or SLiM?

If you really want to remove the user list from GDM, though, look [here.]("http://www.google.com/#hl=en&safe=strict&sa=X&ei=zL_DT9uJI430sQL7hNjYCQ&ved=0CAUQBSgA&q=how+to+remove+username+list+from+gdm&spell=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=99407a7d8742de4a&biw=1176&bih=767&safe=strict")
????

---

### Post by flabdablet on 2012-05-29
cortman, gdmsetup doesn't affect gdm3 as far as I know. Works only on the now obsolete and unsupported gdm.

goneskiing, you can uninstall the gdm3 package and replace it with slim or lightdm as suggested. However, you may have trouble with user switching (multiple concurrent login sessions) if you do. I believe there are still kinks being ironed out of support for that in non-gdm login managers.

---

### Post by cortman on 2012-05-29
> **flabdablet said:**
> cortman, gdmsetup doesn't affect gdm3 as far as I know. Works only on the now obsolete and unsupported gdm.

goneskiing, you can uninstall the gdm3 package and replace it with slim or lightdm as suggested. However, you may have trouble with user switching (multiple concurrent login sessions) if you do. I believe there are still kinks being ironed out of support for that in non-gdm login managers.

Most of the links on the page I linked to suggest using gconf editor, which as far as I know still works with GDM3.

---

### Post by dcstar on 2012-05-29
> **goneskiing said:**
> is there any way to eliminate gdm 3 or get rid of the user list ?

having user names listed on gdm 3 is a major security issue - it takes away 1 level of security (knowing user names) which means an exponential difference in hacking combinations

thru lots of searching, there seems no way to eliminate usernames from showing - this code must be really buried. 

and there seems to be lots of people complaining about this with no one able to resolve it

And whoever put this into gdm 3 should be kicked off the committer list for intentionally diminishing security plus intentionally making it so nearly impossible to correct.  Plus, they have wasted lots of programmers valuable time, searching in vain to correct this.

Less useless complaining and a few minutes web searching would be far more productive:

[http://www.tejasbarot.com/2012/04/25/howto-hide-users-list-from-login-screen-ubuntu-12-04-precise-pangolin-linux/](http://www.tejasbarot.com/2012/04/25/howto-hide-users-list-from-login-screen-ubuntu-12-04-precise-pangolin-linux/)

---

