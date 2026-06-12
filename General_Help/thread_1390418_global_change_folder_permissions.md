---
title: "global change folder permissions"
date: 2010-01-25
forum: General Help
---

### Post by wyomingpat on 2010-01-25
Moved my home to another partition. The folders have permissions set to root so when I logged in I was met by a blank desktop with no menus.

How can I global change the permissions of all folders and files to my user please?

---

### Post by sisco311 on 2010-01-25
> **wyomingpat said:**
> Moved my home to another partition. The folders have permissions set to root so when I logged in I was met by a blank desktop with no menus.

How can I global change the permissions of all folders and files to my user please?

```
sudo chown -R **username**\: /home/**dirname**
```
replace username with your login name and /home/direname with the path to the home directory.

Be careful, don't change the owner of system files.

---

### Post by ibuclaw on 2010-01-25
> **sisco311 said:**
> ```
sudo chown -R **username**\: /home/**dirname**
```
replace username with your login name and /home/direname with the path to the home directory.

Be careful, don't change the owner of system files.

Hmm... not sure why you have the escape there. ;)

Usually, you'll want the group to be set to yourself too.
```
sudo chown -R **username**:**username** /home/**dirname**
```

Regards
Iain

---

### Post by sisco311 on 2010-01-25
> **tinivole said:**
> Hmm... not sure why you have the escape there. ;)

You don't have to; (don't ask me why) but bash auto-complete does escape it.

> **tinivole said:**
> 
Usually, you'll want the group to be set to yourself too.
```
sudo chown -R **username**:**username** /home/**dirname**
```

Regards
Iain

If a colon (or a period) but no group name follows the user name, that user is made the owner of the files and the group of the files  is  changed  to that  user's  login  group.

---

