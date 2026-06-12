---
title: "Can't access account, encrypted home folder"
date: 2010-11-25
forum: General Help
---

### Post by Oven Glove on 2010-11-25
I've done something a bit stupid. I've already encrypted my home folder and just set it to log in without requesting my password. When i do log in now, no startup sound plays, several error messages appear but no desktop. I think it's because I now don't have an opportunity to enter my home folder password, and it doesn't work at all.

Is there any way to edit account settings from 'root' or anything because this really has crippled my computer.

Thanks,
Owen.

---

### Post by Gunman1982 on 2010-11-25
First of all: Setting your desktop to login without challenging you for a password makes a password encrypted home rather futile doesn't it?

You could try to log in via the console, meaning: When your Pc boots up, wait until it tries to log you in, ignore the error messages and press 'CTRL+ALT+F1' which takes you to the tty1 terminal. There you can log in with your normal username password (password is not displayed, not even with stars so don't be irritated when you type it in). I would then kill your X-Server with the command 'sudo killall gdm' and the execute 'startx' this should start gnome again without challenging you for a password. Now you can change the settings back from auto login to the standard with password challenge.
Now you can restart if you want.

---

### Post by Oven Glove on 2010-11-26
Thanks so much got it fixed again now. No idea why I did this in the first place but never mind.

Thanks.

---

