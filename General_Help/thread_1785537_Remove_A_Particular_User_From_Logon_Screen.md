---
title: "Remove A Particular User From Logon Screen"
date: 2011-06-18
forum: General Help
---

### Post by GodveX on 2011-06-18
Since i installed oracle xe and sql developer a user named oracle is now displaying on the log on screen.

I have been playing around trying to figure out if it is possible to remove that user only from the users list on the log on screen in ubuntu.

So far i have only found out how to hide the user list and i also tried to give the user id of oracle below 999 to make it not display this also failed.

do you guys have any solutions for this problem please ?

---

### Post by Krytarik on 2011-06-18
Add the "Exclude" option with the concerning username to your "/etc/gdm/custom.conf" as described here:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)

Greetings.

---

### Post by GodveX on 2011-06-18
thanks for your reply mate it had lots of useful information i did not know about i fixed the problem now thanks to your link

Solution to hide a particular user from the list:
if you have /etc/gdm/custom.conf already edit that one and if you do not already have that file then in the terminal add this
```
sudo cp /usr/share/doc/gdm/examples/custom.conf /etc/gdm/custom.conf
```

When you open the file you have just created or already have then find the section that displays [Greeter] and add this line below it
```
Exclude=user1,user2,nobody
```

N.B: user1 = add a username you don't want to view in the list
     user2 = add another user you don't want to view in the list (can be left out if not needed)
     nobody = this must be done since when you add a user to be excluded you will then see that you now have nobody as a user in the user list this is to remove it to

hope this piece of information will help out a beginner just like myself

---

