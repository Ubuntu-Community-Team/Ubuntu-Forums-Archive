---
title: "can't uninstall mysql"
date: 2011-02-12
forum: General Help
---

### Post by Pacopag on 2011-02-12
Hi.  I installed mysql via

sudo apt-get install mysql-server mysql-client

sudo apt-get install php5-mysql

But when I try to use it, it would say that my password was no good.  So my plan was to remove it, then reinstall it in order to reset the password.  But I needed the password to remove it, which I didn't have, so the remove seemed to fail.  Here's some output:

paco@magnetboxtogo:~$ sudo apt-get remove php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5-mysql is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mysql but it is not going to be installed or
                       php5-mysqli but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

paco@magnetboxtogo:~$ sudo apt-get remove mysql-server mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mysql but it is not going to be installed or
                       php5-mysqli but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I'd like to clean the slate, and re-install it more carefully.  I could've sworn I used my usual password, but it didn't work.  I also tried "root" for the password, but that didn't work either.  It's all screwed up now.  Thanks for any help.

---

### Post by asmoore82 on 2011-02-12
Try ```
sudo apt-get -f install
``` with no packages.

---

### Post by Pacopag on 2011-02-12
Thanks for your reply.  I ran it, and it looked successful.  But what did that do.  What should I do next?

---

### Post by nmaster on 2011-02-12
Don't ignore error messages!!! As Prof. Paul Hilfinger says, "That's for civilians." ;)

The error message you got from apt-get told you exactly what to do.  You have now run 'apt-get -f install'.  I'm assuming that everything went well with that...

Now all you have to do is run 'sudo apt-get remove mysql-server'.  That should do the trick.

---

### Post by Pacopag on 2011-02-12
Cool. Worked.  Now I'm gonna try re-installing it.....

Great!.  Installed and I'm connected.  Thanks a ton.

---

### Post by asmoore82 on 2011-02-12
:popcorn:

---

