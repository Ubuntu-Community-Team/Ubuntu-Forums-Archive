---
title: "looking at other users desktops from root?"
date: 2011-03-11
forum: General Help
---

### Post by Adrienk on 2011-03-11
any way to see other users and there desktop and home folder content from root?

---

### Post by tordeu on 2011-03-11
I am not sure what you mean. Do you just want to be able to see which files are on the Desktop of other users?

If so, then the home folders of the users are located at /home/<username> and the Desktop of users is located at /home/<username>/Desktop. Do you mean something like that?

---

### Post by WorMzy on 2011-03-11
```
ls /home/username
```
```
ls /home/username/Desktop
```

---

### Post by Adrienk on 2011-03-11
so if I go (logged in as root) to the user names home folder i can see all there folders and contents and all the things they have - such as documents in the documents folders, files on the desktop? (through the desktop folder?)

---

### Post by PoHandle on 2011-03-11
Yes, you can use the methods suggested by WorMzy and tordeu to view other user's home folders.  However, if those users had set up their accounts to have an encrypted home folder, you will not be able to view their files and folders.  You'll need their login credentials to decrypt their home folder.

---

