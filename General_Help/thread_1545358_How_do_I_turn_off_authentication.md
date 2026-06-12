---
title: "How do I turn off authentication?"
date: 2010-08-03
forum: General Help
---

### Post by Medical College of VA on 2010-08-03
How do I turn off the authentication feature?  I am the only person who uses my computer and it is frustrating always having to type in my authentication password.  Can I turn off the authentication feature permanently so I am never asked for authentication ever again?

Thank You

---

### Post by mike555 on 2010-08-03
search the forums for this info ,there are a few ......... but you will find it is just stupid thing to do ......
   that said , you can have Ubuntu log in automatically or just use a simple password like " qqqqqq " or something like that........

---

### Post by Medical College of VA on 2010-08-03
> **mike555 said:**
> search the forums for this info ,there are a few ......... but you will find it is just stupid thing to do ......
   that said , you can have Ubuntu log in automatically or just use a simple password like " qqqqqq " or something like that........

Why do I need to constantly type in a password for a computer that never leaves my house?  Will my birds hack into it?  (They have pulled several notebook keys though.)  It is a waste of my time to setup a password to prevent myself from getting into it.

Furthermore, I searched this forum for an answer and it does not exist and typing in a simple password like 123 or qqqqqq does not work with 10.04.  Maybe you need to search before typing in answers.

---

### Post by Quackers on 2010-08-03
This subject was discussed at length in this thread
[http://ubuntuforums.org/showthread.php?t=1541085&highlight=user+password](http://ubuntuforums.org/showthread.php?t=1541085&highlight=user+password)

---

### Post by Maverick_Meerkat on 2010-08-03
Greetings,

On the desktop drop down menu navigate

System>Administration>Login Screen

From here you can set the system to automatically log in. However, anytime you perform a task that requires admin or elevated privileges you will still be asked for a password.

I do not know of any way to disable or remove the authentication feature completely, but there is a work around. Rather than logging in under your username, you can log in as root. Although, this is (Officially) not recommended. Nor do I endorse the practice. Still, it is you computer and your choice.
;)

---

### Post by TXpaniolo on 2010-08-03
Go to System Preferences Screensaver and uncheck lock keyboard when screensaver is active and you won't need your password to turn off screen saver.  Also there is a checkbox in System Administration Users and Groups under the change password box where you can check do not ask for password on login.

I have kids around, and to stop myself from making potential major changes I set up a second user with a simple pattern password that only has user access.   I only input it on startup or login.  Whenever I need to do admin I either input the password or change to my Admin user.

---

### Post by dragos240 on 2010-08-03
You can also edit /etc/shadow

---

### Post by Medical College of VA on 2010-08-03
I was searching the wrong term.  Thank you for the answers.

---

