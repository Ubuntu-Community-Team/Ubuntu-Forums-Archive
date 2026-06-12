---
title: "sudo vs. su -"
date: 2010-07-19
forum: General Help
---

### Post by McRat on 2010-07-19
Not sure what the difference is.  I've read some posts that say to use the "su -" command.

When I type "su - " it asks for a password, I type in the system password, and it says 'wrong password'.

Just curious what the difference between the two is.

---

### Post by sisco311 on 2010-07-19
su prompts for the target user's password. Since the root account password is locked by default, you can not use su to become the root user.

See:
[uhelp]community/RootSudo[/uhelp]

Instead of **su -**, use:
```
sudo -i
```
type:
```
exit
```or press Ctrl+d to log out from the root shell.

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see: [unutbu's](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4) post

---

### Post by RiceMonster on 2010-07-19
su is short for "substitute user". If I want to switch to the user "vanessa" on the command line, I would type:
```
su vanessa
```

If I type su with a - or no parameters, it will default to the root account, which has a different password than your account. On Ubuntu, the root account is locked, so you run root commands with "sudo". Sudo allows giving users the ability to run specific commands with root privilages, and on Ubuntu it's configured to give any user in the admin group to run any command with it.

---

### Post by McRat on 2010-07-19
Thanks!  So I didn't "lose" a password, it just isn't necessary to use "su" with Ubuntu.

---

