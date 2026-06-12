---
title: "Ubuntu booting in Command Line Instead of GUI"
date: 2011-08-13
forum: General Help
---

### Post by vikasgoel.007 on 2011-08-13
I have Ubuntu 10.10 Installed on my computer along with Window 7

While booting from grub (to choose from Windows or Ubuntu). I highlighted on the Ubuntu option and pressed 'e' and since then each time I try logging in to the Ubuntu, it gives me a command line interface instead of GUI.

Can anyone tell me how to get back the GUI for Ubuntu.

Thank You

---

### Post by wojox on 2011-08-13
What did you change? "e" means edit so must of edited something.

Try:

```
startx
```

---

### Post by vikasgoel.007 on 2011-08-13
I couldn't remember the password for root. So i went to Ubuntu and then pressed 'e'.

After that i typed 'single'. And a command line interface came. Then i typed:
"passwd root"
and tried changing the password for the root user. The password did not change. Instead now each time I try logging into Ubuntu, it gives a command line interface only.

And what is startx?

---

### Post by -kg- on 2011-08-13
"startx" ***_should_*** start XWindow, which is what the GUI uses to supply the "Goo", so to speak. :P

Of course, the "root" password is the password you supplied at installation time, and is the password you use to log onto the system, unless you have multiple users, or supplied a different password at one point to log on to your "User" account that is different than the "root" password.

It's highly suggested that you don't forget your root password, as you've found out!  I'm pretty sure that you need that password to change that password, which is probably why you couldn't change it.

I suggest you remember it; otherwise you're looking at a re-install.  And if you do, I suggest that you write it down or something.  You now know how important it is!

Of course, someone might come along with better news for you, but.... [IMG]http://www.bdwf.net/forum/images/smilies/smiley_shrug%5B1%5D.gif[/IMG]

---

### Post by wojox on 2011-08-13
So you have a root password and a user password?

Try this [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

