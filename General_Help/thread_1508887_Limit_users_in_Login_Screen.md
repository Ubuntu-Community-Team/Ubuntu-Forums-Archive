---
title: "Limit users in Login Screen"
date: 2010-06-13
forum: General Help
---

### Post by jamesdcarroll on 2010-06-13
I have a fair number of users created for running processes (apache, oracle, etc) and they appear in the login screen when I boot.

Is there a way to not display them? 

Thanks,

---

### Post by lunatico on 2010-06-18
I'm also looking for an answer to this. When I find it I'll post it here.

---

### Post by lunatico on 2010-06-18
God this is why I love Linux and specially Ubuntu, everything is possible and so easy!

So to limit the users shown in the login screen, the theory is that users with a UserID => 1000 are shown in the login screen and users with a UserID <= 999 are not shown in the login screen.

[LIST=1]
[*]System -> Administration -> Users and Groups -> 'Click to make changes'
[*]Select the user you want to remove from the login screen and go to Properties.
[*]Go to the Advanced tab and change the User ID to something lower than 999.
[/LIST]

**Tip:** On a terminal do ***cat /etc/passwd | grep xxx*** where xxx is the new ID you want to give to that user, this is to make sure the ID isn't taken by some other user already.

**Note:** Once you have changed your users IDs to be lower than 999 they will not show in the 'User Settings' GUI. You will have to use command line to modify them.

---

### Post by jamesdcarroll on 2010-06-20
Thanks! That works, but there has to be more to it. Root has a USERID = 0 and it doesn't show up in the login screen and is visable in the 'Users and Groups' applet. There must be a flag or something somewhere that can be flipped. Like you said: "everything is possible"

---

### Post by lunatico on 2010-06-20
I'm glad that worked. Yes there might be more to it... or maybe not, I mean root is like God so it could very well be hardcoded... dunno.

---

