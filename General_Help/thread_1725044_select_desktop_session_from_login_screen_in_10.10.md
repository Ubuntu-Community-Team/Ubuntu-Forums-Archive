---
title: "select desktop session from login screen in 10.10"
date: 2011-04-09
forum: General Help
---

### Post by Maverickprowls on 2011-04-09
Hi there,

I've been googling about a bit and can't find an answer to this question.  Even a post saying "you can't do this anymore" would have satisfied!

I've installed unity desktop on a standard desktop installation of Maverick Meerkat.  I am able to change which desktop session opens on logon through System > Administration > Login Screen which is fine but a little cumbersome. However, there doesn't seem to be any way to choose my desktop session from the login screen itself.  I've tried all the menu options in the aforementioned settings tool, and all I'm shown at the login prompt are the User Assistance icon and the shutdown/reboot button.  I seem to recall that there were a lot more options on that screen in previous versions.

Any help would really be appreciated, thanks!

---

### Post by ~Plue on 2011-04-09
the 'session:' option would only appear once you select the user from the list.

user selected:
[http://www.debianadmin.com/wp-content/gallery/1004/1.png](http://www.debianadmin.com/wp-content/gallery/1004/1.png)
what you seem to be experiencing:
[http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg](http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg)

---

### Post by owenll on 2011-04-09
Just in case you haven't seen these - there are more options on the bottom of the login screen

---

### Post by Maverickprowls on 2011-04-09
> **owenll said:**
> Just in case you haven't seen these - there are more options on the bottom of the login screen

Thanks for the reply - but there aren't any other options at the bottom of my screen.

---

### Post by Maverickprowls on 2011-04-09
> **~Plue said:**
> the 'session:' option would only appear once you select the user from the list.

use selected:
[http://www.debianadmin.com/wp-content/gallery/1004/1.png](http://www.debianadmin.com/wp-content/gallery/1004/1.png)
what you seem to be experiencing:
[http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg](http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg)

Oh right, thanks for this. So if I've disabled the user list (i.e. if I'd like my users to type their username in) then there's no way to view the desktop session options?

---

### Post by ~Plue on 2011-04-09
> **Maverickprowls said:**
> Oh right, thanks for this. So if I've disabled the user list (i.e. if I'd like my users to type their username in) then there's no way to view the desktop session options?
if they still require to enter the password, then it should be possible. else it'll pass too fast to change anything

---

### Post by Maverickprowls on 2011-04-09
> **~Plue said:**
> if they still require to enter the password, then it should be possible. else it'll pass too fast to change anything

That's solved it for me!  Thanks very much.

To summarise for anyone who comes across this thread:

I had my machine set up so it didn't require a password for a certain user.  The series of options for picking your desktop session only appear after you've entered the username you'd like to log in as, so I never saw the options until I disabled the passwordless login.

Thanks again to everyone for helping me out

---

