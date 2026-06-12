---
title: "login problem"
date: 2010-09-06
forum: General Help
---

### Post by Innigo on 2010-09-06
I recently restarted my 10.04 Ubuntu after editing .profile and now I can't login. It' doesn't say "Authentication failure" as it does if I enter a wrong password, instead the screen just goes black for 2s and then it returns to the login prompt without letting me in. 

The change I made to .profile was:
$APP_ROOT="/home/me/app/app3-1.4"
PATH = "$APP_ROOT:$PATH"
export PATH

Is there something wrong with this? I don't know what's gone wrong or why it would do this.

---

### Post by anglican on 2010-09-06
> **Innigo said:**
> I recently restarted my 10.04 Ubuntu after editing .profile and now I can't login. It' doesn't say "Authentication failure" as it does if I enter a wrong password, instead the screen just goes black for 2s and then it returns to the login prompt without letting me in. 

The change I made to .profile was:
$APP_ROOT="/home/me/app/app3-1.4"
PATH = "$APP_ROOT:$PATH"
export PATH

Is there something wrong with this? I don't know what's gone wrong or why it would do this.
Yes, the first line should be:

```
APP_ROOT="/home/me/app/app3-1.4"
```(i.e. no "$" at the beginning, you have to set APP_ROOT to something before you can use it). If you can't login now you'll have to boot from the live CD and correct your .profile.

H

---

### Post by linux-hack on 2010-09-06
When you declare a variable you don't put the $ before that is just when you use to get the variable value.

---

### Post by Innigo on 2010-09-06
Thanks guys, 
the $APP_ROOT was somehow preventing the GUI from going. I managed to get ye old tty login prompt by using Ctrl-Alt-F1 after someone told me about that. Then I just edited out the offending lines in .profile 
then
$bash .profile
restart
;)

---

