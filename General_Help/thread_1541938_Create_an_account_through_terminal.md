---
title: "Create an account through terminal"
date: 2010-07-29
forum: General Help
---

### Post by redfox1160 on 2010-07-29
How do I create a user account through the terminal? I want to make a guest account that cant be seen at the login screen (so that you have to click other and type in the credentials). Thanks!

---

### Post by nmaster on 2010-07-29
> **redfox1160 said:**
> How do I create a user account through the terminal? I want to make a guest account that cant be seen at the login screen (so that you have to click other and type in the credentials). Thanks!

nice job taking the time to learn the command line.  if you really want to be "legit" you shouldn't be reliant on a GUI.

bad job using google though.  here is a great custom search that i use: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

that's how i found this answer quickly: [https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)

EDIT: My mistake! i didn't read you're post properly.  the link above will show you how to make a new user, but i'm not sure how to hide it from GDM.

---

### Post by prodigy_ on 2010-07-29
User accounts with UID < 1000 aren't shown in gdm login screen. So (assuming that your guest user name is **guest**), the command is:
```
sudo usermod -u 999 guest
```
You can use any number that is less than 1000. Just make sure it's not in use already: ```
cat /etc/passwd
``` will show you the list of all users and their UIDs.

---

### Post by redfox1160 on 2010-07-29
> **prodigy_ said:**
> User accounts with UID < 1000 aren't shown in gdm login screen. So (assuming that your guest user name is **guest**), the command is:
```
sudo usermod -u 999 guest
```
You can use any number that is less than 1000. Just make sure it's not in use already: ```
cat /etc/passwd
``` will show you the list of all users and their UIDs.

Thanks

---

