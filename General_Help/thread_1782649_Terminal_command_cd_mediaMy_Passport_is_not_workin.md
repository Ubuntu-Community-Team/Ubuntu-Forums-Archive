---
title: "Terminal command: cd /media/My Passport is not working"
date: 2011-06-14
forum: General Help
---

### Post by emergingtechnologies on 2011-06-14
The drive is mounted, and I'm saving files to it, but I can't navigate to it in terminal with the cd command.  I can access other USB drives.  Is it the space in the drive name?  Can someone help me access the directory?  Thanks.

---

### Post by Keypel on 2011-06-14
yes, its that darn pesky space between My and Passport.

cd media/My\ Passport/

tip: use the TAB key. It will auto complete what your typing. 

i.e type cd [COLOR="Red"]m[/COLOR] (for [COLOR="Red"]m[/COLOR]edia) and hit TAB. it automatically fills in cd media/. Then hit [COLOR="#ff0000"]M[/COLOR] (for [COLOR="#ff0000"]M[/COLOR]y Passport) and hit TAB again and it fills in cd media/My\ Passport/

Sometimes you have to type the first two letters. For Example Desktop and Downloads both start with D so if you want Desktop type cd De [TAB]

---

### Post by emergingtechnologies on 2011-06-14
Thank you so much!  It is these frustrating little tweaks that make transitioning to Ubuntu a challenge for some.  That was a great answer!  I'll pop it into my bag of tricks!

---

### Post by Keypel on 2011-06-14
No problem, glad I could give back to the community.

---

